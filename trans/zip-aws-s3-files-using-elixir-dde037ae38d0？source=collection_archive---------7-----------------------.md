# 使用 Elixir 压缩 AWS S3 文件

> 原文：<https://medium.datadriveninvestor.com/zip-aws-s3-files-using-elixir-dde037ae38d0?source=collection_archive---------7----------------------->

## 关于如何为 AWS S3 文件创建 zip 服务的一些提示。

![](img/e2689ce1cc2f5160eaf64ac46bef9585.png)

Image by Romain Hiest - Pixabay.

该服务必须从 S3 桶中下载一个由 POST 请求中的“aws key”表示的文件，压缩并上传，将压缩后的文件返回到桶中。

为了访问 AWS S3，我们使用[**ex _ AWS**](https://hexdocs.pm/ex_aws/ExAws.html)e[**ex _ AWS _ S3**](https://hexdocs.pm/ex_aws_s3/ExAws.S3.html)。

该服务提供一个端点来接收 POST `{ "params": { "aws_s3_key": "aws_key_from_your_file" } }`。

将接收到的 aws 密钥插入到队列中，由 [**百老汇**](https://hexdocs.pm/broadway/Broadway.html) 进行处理。

> 百老汇是一个并行、多阶段的工具，用于构建数据接收和数据处理管道。
> 
> 它允许开发人员高效地使用来自不同来源的数据，如亚马逊 SQS、Apache Kafka、Google Cloud PubSub、RabbitMQ 等。

百老汇需要一个消息队列，我使用了基于博客 [**、RabbitMQ 和长生不老药**](https://akoutmos.com/post/broadway-rabbitmq-and-the-rise-of-elixir/) 的 [**RabbitMQ**](https://hexdocs.pm/broadway/rabbitmq.html) 。

## 创建队列

我需要 3 个新队列:

*   *presigned_queue* —接收用户的请求参数；
*   *downloaded_queue* —下载文件和 zip
*   *uploaded_queue* —上传 zip 到 S3。

如何创建您的队列？[看这里……](https://hexdocs.pm/broadway/rabbitmq.html#content)。

```
defmodule MyZip.RMQPublisher do
  [@behaviour](http://twitter.com/behaviour) GenRMQ.Publisher @rmq_uri “amqp://rabbitmq:rabbitmq@localhost:5672”
  @hn_exchange “something”
  @presigned_queue “presigned_queue”
  @downloaded_queue “downloaded_queue”
  @uploaded_queue “uploaded_queue”
  @publish_options [persistent: false] def init do
    create_rmq_resources()
    [
      uri: [@rmq_uri](http://twitter.com/rmq_uri),
      exchange: [@hn_exchange](http://twitter.com/hn_exchange)
    ]
  end def start_link do
    GenRMQ.Publisher.start_link(__MODULE__, name: __MODULE__)
  end def publish_presigned_queue(data) do
    GenRMQ.Publisher.publish(__MODULE__, data, @presigned_queue, @publish_options)
  end def publish_downloaded_queue(data) do
    GenRMQ.Publisher.publish(__MODULE__, data, @downloaded_queue, @publish_options)
  end def publish_uploaded_queue(data) do
    GenRMQ.Publisher.publish(__MODULE__, data, @uploaded_queue, @publish_options)
  end def presigned_queue, do: [@presigned_queue](http://twitter.com/presigned_queue)
  def downloaded_queue, do: [@downloaded_queue](http://twitter.com/downloaded_queue)
  def uploaded_queue, do: [@uploaded_queue](http://twitter.com/uploaded_queue) defp create_rmq_resources do
    {:ok, connection} = AMQP.Connection.open([@rmq_uri](http://twitter.com/rmq_uri))
    {:ok, channel} = AMQP.Channel.open(connection) AMQP.Exchange.declare(channel, @hn_exchange, :topic, durable: true) AMQP.Queue.declare(channel, @presigned_queue, durable: true)
    AMQP.Queue.declare(channel, @downloaded_queue, durable: true)
    AMQP.Queue.declare(channel, @uploaded_queue, durable: true) AMQP.Queue.bind(channel, @presigned_queue, @hn_exchange, routing_key: @presigned_queue)
    AMQP.Queue.bind(channel, @downloaded_queue, @hn_exchange, routing_key: @downloaded_queue)
    AMQP.Queue.bind(channel, @uploaded_queue, @hn_exchange, routing_key: @uploaded_queue) AMQP.Channel.close(channel)
  end
end
```

## 处理器已辞职

创建队列后，我定义了一个百老汇来使用 ***预签名 _ 队列*** 队列。

```
defmodule MyZip.ProcessorPresigned do
  use Broadway alias Broadway.Message ... start_link ... def handle_message(_, %Message{data: data} = message, _) do # Get the key in the queue
    aws_s3_key =
      data
      |> Jason.decode!
      |> get_in([“aws_s3_key”]) # Creates a presigned_url to download the file
    url = 
      ExAws.Config.new(:s3)
      |> ExAws.S3.presigned_url(:get, “my_bucket”, aws_s3_key,[expires_in: 300])
      |> case do
        {:ok, url} -> url
      end # Send the presigned key and url to the queue *downloaded_queue*
    %{url: url, key: aws_s3_key }
    |> Jason.encode!
    |> MyZip.RMQPublisher.publish_downloaded_queue message
 end
```

## 处理器下载

我们现在需要一个百老汇来处理***downloaded _ queue***，下载文件并生成一个 zip 文件。

```
defmodule MyZip.ProcessorDownload do
  use Broadway alias Broadway.Message ... start_link ... def handle_message(_, %Message{data: data} = message, _) do
    %{“key” => key, “url” => url} =
      data |> Jason.decode! # Download file from AWS S3
    file_downloaded = MyZip.HTTPDownloadStream.get(url) # Create a temporary zip file
    {:ok, zip_path} = Briefly.create

    # ZIP files
    Zstream.zip(
      [ Zstream.entry(key, file_downloaded) ]
    )
    |> Stream.into(File.stream!(zip_path))
    |> Stream.run() MyZip.RMQPublisher.publish_uploaded_queue(zip_path) message
  end
end
```

## 下载文件

为了下载 S3 文件，我们使用了函数`HTTPDownloadStream.get/1`。该功能基于博客[**{ PoetiCoding }**](https://www.poeticoding.com/elixir-streams-to-process-large-http-responses-on-the-fly/)上显示的实现，使用`Stream.Resource`并异步下载。

```
defmodule MyZip.HTTPDownloadStream do
  def get(url) do
    Stream.resource(
      fn -> start_fun(url) end,
      fn %HTTPoison.AsyncResponse{}=resp ->
        handle_async_resp(resp,emit_end)
        {:end, resp}->
          {:halt, resp}
      end, fn %HTTPoison.AsyncResponse{id: id} ->
        :hackney.stop_async(id)
      end
    )
  end defp start_fun(url) do
    HTTPoison.get!(url,%{}, [stream_to: self(), async: :once])
  end defp handle_async_resp(%HTTPoison.AsyncResponse{id: id}=resp,emit_end) do
    receive do
      %HTTPoison.AsyncStatus{id: ^id, code: code}->
        HTTPoison.stream_next(resp)
        {[], resp}
      %HTTPoison.AsyncHeaders{id: ^id, headers: headers}->
        HTTPoison.stream_next(resp)
        {[], resp}
      %HTTPoison.AsyncChunk{id: ^id, chunk: chunk}->
        HTTPoison.stream_next(resp)
        {[chunk], resp}
      %HTTPoison.AsyncEnd{id: ^id}->
        if emit_end do
          {[:end], {:end, resp}}
        else
          {:halt, resp}
        end
    after
      5_000 -> raise “receive timeout”
    end
  end
end
```

## 处理器加载

下载完成后，我们创建了一个临时文件来存储 zip 文件，简单来说使用[](https://github.com/CargoSense/briefly)**。并且我们用 [**ZStream**](https://hexdocs.pm/zstream/Zstream.html) 压缩文件。压缩文件的路径被发送到 ***uploaded_queue*** 。**

**然后百老汇处理了 ***上传 _ 队列*** 。**

```
defmodule MyZip.ProcessorUpload do
  use Broadway alias Broadway.Message ... start_link ... def handle_message(_, %Message{data: data} = message, _) do
    data
    |> ExAws.S3.Upload.stream_file
    |> ExAws.S3.upload(“my-bucket-zip”, "zip-name.zip")
    |> ExAws.request! message
  end
end
```

## **开始**

**我们不能忘记初始化一切。**

```
defmodule MyZip.Application do
  [@moduledoc](http://twitter.com/moduledoc) false use Application def start(_type, _args) do
    children = [ ...other things..., %{
        id: MyZip.RMQPublisher,
        start: {MyZip.RMQPublisher, :start_link, []}
      },
      MyZip.ProcessorPresigned,
      MyZip.ProcessorDownload,
      MyZip.ProcessorUpload
    ] opts = [strategy: :one_for_one, name: MyZip.Supervisor]
    Supervisor.start_link(children, opts)
  end
end
```

## **属国**

```
defmodule MyZip.MixProject do
  use Mix.Project .... defp deps do
    [
      {:phoenix, “~> 1.5.7”}, ....others dependencies..., {:jason, “~> 1.1.2”},
      {:broadway, “~> 0.4.0”},
      {:broadway_rabbitmq, “~> 0.4.0”},
      {:gen_rmq, “~> 2.3.0”},
      {:ex_aws, “~> 2.0”},
      {:ex_aws_s3, “~> 2.0”},
      {:httpoison, “~> 1.8”},
      {:sweet_xml, “~> 0.6.6”},
      {:zstream, “~> 0.5.2”},
      {
        :briefly,
        git: “[https://github.com/CargoSense/briefly](https://github.com/CargoSense/briefly)”,
        ref: “2526e9674a4e6996137e066a1295ea60962712b8”
      }
    ]
  end
end
```

## **怎么考？**

**为了测试我创建了一个文件 ***ab。JSON*** 项目*的根源。***

```
{ 
  “params”: { 
    “type”: “asset”,
    “aws_s3_key”: “77d346e5072f315869909ffdd692d91c.JPG”}
}
```

**我执行了:**

```
ab -c 1 -n 10 -p ab.json -T application/json — verbose [http://127.0.0.1:4000/api/zip](http://127.0.0.1:4000/api/zip)
```

**希望这对你有帮助。尽情享受吧！！**