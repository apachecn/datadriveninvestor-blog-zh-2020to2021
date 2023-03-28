# Docker 上的数据库

> 原文：<https://medium.datadriveninvestor.com/databases-on-docker-d94e1df3903?source=collection_archive---------15----------------------->

![](img/24b1661d02c6e570df55360751e70728.png)

Photo by [fabio](https://unsplash.com/@fabioha?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

在本文中，我将介绍 Docker 在 Redhat 8.1 上的安装过程。然后我将向您展示如何在我们的 Docker 环境上部署不同的数据库(Oracle、IBM DB2、MySQL、PostGres、MongoDB)。

## 安装 Docker

在启动之前设置您的 yum 存储库，并确保您的 servert 连接到 internet。

```
# mkdir /tmp/docker
# cd /tmp/docker
# wget [-k https://raw.githubusercontent.com/sbaiidrissiyoussef/Docker/master/install_docker.sh](https://raw.githubusercontent.com/sbaiidrissiyoussef/Docker/master/install_docker.sh)
# chmod u+x /tmp/docker/install_docker.sh
# /tmp/docker/install_docker.sh
```

安装完成后，通过运行 hello-world 映像来验证您的 Docker 版本和完整性环境

```
# docker --version
# docker run hello-world
```

现在，在正确设置 docker 环境之后，我们将在其中部署不同的数据库。

在开始之前，确保你在[https://hub.docker.com/](https://hub.docker.com/)有一个码头工人账户

[](https://www.datadriveninvestor.com/2019/02/25/6-alternatives-to-the-yahoo-finance-api/) [## 雅虎财经 API |数据驱动投资者的 6 种替代方案

### 长期以来，雅虎金融 API 一直是许多数据驱动型投资者的可靠工具。许多人依赖于他们的…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/25/6-alternatives-to-the-yahoo-finance-api/) 

## Docker 上的 Oracle 数据库

下面的步骤描述了在我们的 docker 环境中部署 Oracle 数据库 12.0.0.1

```
# docker login###### Setup Environment Variables# DB_NAME=ODB1
# DB_PORT=1521
# DB_HOME=/home/oracle/oradata###### Deploy your Database Image# docker run -d -it --name $DB_NAME -p $DB_PORT:$DB_PORT -v $DB_HOME:$DB_HOME store/oracle/database-enterprise:12.2.0.1
```

部署数据库容器后，您可以使用以下命令访问您的 shell

```
# docker exec -it $DB_NAME /bin/bash
```

## Docker 上的 IBM DB2

下面的步骤描述了 IBM DB2 数据库的部署

```
###### Setup Environment # mkdir /tmp/Docker
# cd /tmp/Docker
# docker login
# docker pull ibmcom/db2
# touch .env_list###### Create an Env File using the following command :echo -e 'LICENSE=accept
DB2INSTANCE=db2inst1
DB2INST1_PASSWORD=password
DBNAME=testdb
BLU=false
ENABLE_ORACLE_COMPATIBILITY=false
UPDATEAVAIL=NO
TO_CREATE_SAMPLEDB=false
REPODB=false
IS_OSXFS=false
PERSISTENT_HOME=false
HADR_ENABLED=false
ETCD_ENDPOINT=
ETCD_USERNAME=
ETCD_PASSWORD=' >> .env_list###### Deploy your Database Image# docker run -h db2server --name db2server --restart=always --detach --privileged=true -p 50000:50000 --env-file .env_list -v /Docker:/database ibmcom/db2
# docker exec -ti db2server bash -c "su – db2inst1"
```

## Docker 上的 PostgreSQL

这些步骤描述了如何在 docker 环境中部署 PostgreSQL 数据库

```
###### Setup Environment Variables# DB_NAME=postgres-test
# DB_PASSWORD=mysecretpassword
# DB_PORT=5432###### Deploy your Database Image # docker run --name $DB_NAME -e POSTGRES_PASSWORD=$DB_PASSWORD -d -p $DB_PORT:$DB_PORT -v $HOME/docker/volumes/postgres:/var/lib/postgresql/data  postgres
```

## Docker 上的 MySQL

这些步骤描述了如何在 docker 环境中部署 MySQL 数据库

```
###### Setup Environment Variables# DB_NAME=mysql01###### Deploy your Database Image # docker pull mysql/mysql-server:latest
# docker run --name=$DB_NAME -d mysql/mysql-server:latest
# docker logs $DB_NAME                     ## Get password
# docker exec -it $DB_NAME mysql -uroot -p ## Login to your db
```

## Docker 上的 MongoDB

这些步骤描述了如何在 docker 环境中部署 MongoDB 数据库

```
###### Setup Environment Variables# DB_NAME=mongodb###### Deploy your Database Image# docker pull mongo
# docker run -d -p 27017-27019:27017-27019 --name $DB_NAME mongo:latest
# docker exec -it mongodb bash
```

在 Docker 上部署数据库是构建概念验证甚至开发环境的最佳解决方案，它可以快速部署并易于维护，而我们在设置内部安装时面临的所有问题根本不存在。

~优素福·斯拜·伊德里西，2020