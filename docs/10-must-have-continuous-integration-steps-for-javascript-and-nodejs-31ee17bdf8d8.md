# JavaScript 和 NodeJS 的 10 个必备持续集成步骤

> 原文：<https://medium.datadriveninvestor.com/10-must-have-continuous-integration-steps-for-javascript-and-nodejs-31ee17bdf8d8?source=collection_archive---------3----------------------->

![](img/30a2a34beefc297e9a49ed3affa62218.png)

Photo by [Xavier von Erlach](https://unsplash.com/@xavier_von_erlach?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/cog?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

无论你有一个小的前端服务，一个大的整体，正在构建一个 MVP 或者一个生产级的应用——拥有一个持续的集成服务运行提交将会极大地帮助你的开发速度和质量。

现在的持续集成服务非常容易建立，支持 Dockerfiles，而且非常便宜。它们支持拾取每个代码变更或特定分支，并运行您的脚本，以便您可以对提交的每个代码进行检查，并且永远不会忘记运行您的单元测试。尤其是如果你经常犯错误，这是一个很好的方法来看看哪个改变破坏了什么。

但是你的线人应该做什么样的检查呢？以下脚本面向 JavaScript(和/或 NodeJS)开发人员，尽管最佳实践几乎适用于任何语言和服务。

## 1 |检查第三方包的安全问题

为了确保您意识到潜在的安全问题并能够缓解它们，您可以运行 NPM 的`audit`命令。它会搜索发布您正在使用的第三方软件包(甚至是您的第三方软件包正在使用的那些)，这些软件包已经在他们的数据库中存档，您可以在 https://www.npmjs.com/advisories 的[看到。这意味着它只包括用户报告的问题。](https://www.npmjs.com/advisories)

安全级别遵循 https://www.first.org/cvss/specification-document 的 CVSS()，这意味着对所有重要或关键问题运行您的审计并使用代码`1`退出，您可以在您的配置项中实现以下步骤:

```
npm audit --audit-level=high
```

这将扫描您的软件包并输出所有发现的问题。根据您的依赖项的数量，发现的问题列表可能会很长；如果您只想查看重要和关键问题，可以使用以下命令:

```
npm audit --audit-level=high | grep -E "(High | Critical)" -B3 -A10
```

(在[https://github.com/npm/npm/issues/20596](https://github.com/npm/npm/issues/20596)发现)

除了 NPM(或纱)审计，有更多的方法来搜索安全问题。一般来说，你应该尽可能多地覆盖你的基础设施:从你自己的代码到你的代码正在处理的整个堆栈。

例如，如果你在生产中使用 Docker，你可以运行像 Clair([https://github.com/quay/clair](https://github.com/quay/clair))这样的工具来静态分析你的 Docker 图像。

特别是如果你有 B2B 客户，安全检查对通过他们的审计是很重要的。你可以在 https://medium.com/@Markus.[了解更多关于 B2B 安全审计的信息 Hans lik/what-a-customers-it-security-audit-for-web-apps-is-and-how-to-pass it-b 637 c 9 df 67 a 1](https://medium.com/@Markus.Hanslik/what-a-customers-it-security-audit-for-web-apps-is-and-how-to-pass-it-b637c9df67a1)。

## 2 |检查法律问题

你正在开发不想开源的专有软件吗？那么你一定要确保你遵守你正在使用的第三方软件包的许可。毕竟，如果你是在构建封闭源代码，你是不允许使用一些像 GPL-2 这样的许可证的。

NPM 包`license-checker`遍历您正在使用的所有 NPM 包，可能会因为无效的许可证而失败，这使它成为您的 CI 的完美步骤。

## 3 |检查过期的依赖项

尤其是在短暂的 JavaScript 世界中，包更新非常频繁，有时甚至一天更新多次。

有多种方法可以让您的配置项报告过期的软件包，以便您可以更新它们；最简单的方法是使用 NPM 软件包。

`npm-check-updates`顾名思义，它会检查您的任何第三方 NPM 依赖项是否过期，然后抛出退出代码，以便您的配置项可以提醒您需要更新:

```
ncu --errorLevel 2
```

(如果您计划手动更新软件包，您可能希望将 CI 步骤设置为将来自 NCU 的错误视为警告，这样您的管道不会被阻塞，但您仍然知道需要进行更新。)

除了这种非常手动的方法，还有一些工具可以自动检查更新，甚至支持检查 Dockerfiles 中过时的库等等。查看 renew([https://www . white source software . com/free-developer-tools/renew/](https://www.whitesourcesoftware.com/free-developer-tools/renovate/))或 Snyk ( [https://snyk.io](https://snyk.io) )，它们也支持安全审计。

## 4 | Lint 您的代码以查找编码风格和质量问题

如果你在一个团队中工作，或者即使你只是在一个较长时间跨度的项目中工作，编码风格有可能会偏离，使你的代码难以阅读。手动检查需要时间，并且会降低代码审查的速度。

然而，你可以使用`prettier`([https://prettle . io](https://prettier.io))来确保你所有的文件总是以相同的方式自动格式化。

如果您想在代码格式不正确的情况下使 CI 管道失败，只需使用以下命令(通过 NPM 安装了 prettier 之后):

```
prettier --check “src/**/*.*“ --ignore-unknown
```

ignore-unknown 标志将确保 prettier 只检查它实际上可以格式化的文件，比如 JavaScript、TypeScript、HTML 甚至 YaML。

如果您的 CI 支持在一个步骤中提交代码，您也可以直接修复所有错误:

```
prettier "**/*" --write --ignore-unknown
```

此外，你可以使用`eslint`(【https://eslint.org】)来 lint 你的代码。它现在还支持 TypeScript，所以不再需要安装 TSLint 使用推荐的 ESLint 规则将帮助您发现代码中的潜在问题(例如，getter 函数不返回任何内容)，并遵循最佳实践(例如，不要在条件表达式中赋值以增加可读性)。

一旦通过 NPM 安装并设置了 ESLint，就可以在 CI 步骤中使用以下脚本:

```
npx eslint src --ext .js --format junit > eslint.xml
```

这将对您的带有`js`扩展名的`src`文件夹中的文件运行 ESLint，并以 JUnit 格式输出其结果，这可以被大多数 CI 系统解析。

顺便说一下，如果您想在一个 CI 作业中运行多个脚本，但不希望立即失败，您可以像这样组合退出代码:

```
- RESULT=0
- npx prettier -c ‘src/**/*.*‘ — Ignore-unknown || RESULT=$((RESULT + $?)) || true
- npx eslint src — ext .js — format junit > eslint.xml || RESULT=$((RESULT + $?)) || true
- if [ $RESULT -gt 0 ]; then exit 1; fi
```

## 5 |在您的容器中构建和测试！

您的 CI 渠道支持运行 Docker 容器吗？如果是这样，为了减少出错的空间，并减少代码重复，不要直接在 CI 的标准 runner 映像中运行测试，而是在您的应用程序中使用的实际 Docker 映像中运行测试。

[](https://www.datadriveninvestor.com/2020/12/07/name-matching-techniques-with-python/) [## 使用 Python |数据驱动投资者的名称匹配技术

### 我们确实面临很多情况，我们必须匹配一个有很多变体的单词。这可能是因为错别字…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/12/07/name-matching-techniques-with-python/) 

例如，如果您使用 Bitbucket Pipelines CI 系统，默认情况下，测试步骤可能如下所示(摘自[https://support . atlassian . com/bit bucket-cloud/docs/JavaScript-nodejs-with-bit bucket-Pipelines/](https://support.atlassian.com/bitbucket-cloud/docs/javascript-nodejs-with-bitbucket-pipelines/)):

```
image: node:10.15.0
pipelines:
  default:
    - step:
      script:
        - npm install
        - npm test
```

然而，这将在普通 NodeJS 映像中测试您的代码。如果你正在开发一个做一些图像操作的后端应用程序，你的代码可能使用 ImageMagick，并且在这里失败；即使您的实际生产 Docker 映像可能正确安装了 ImageMagick。

另一种可能导致失败的情况是，您正在更新生产映像的节点版本，但忘记在配置项中执行此操作；您可以在 CI 中通过测试，但是您的代码在生产中可能会失败。

在您的实际容器中运行测试可能如下所示:

```
# First, build the container
- docker build -t $IMAGE_NAME:$IMAGE_TAG .
# Then, run the tests inside your container
- docker run — name $IMAGE_NAME-tester-$IMAGE_TAG $IMAGE_NAME:$IMAGE_TAG sh -c “npm run test“
# Finally, copy the test results from inside your container to the CI, so that you may use it as an artifact
- mkdir -p artifacts
- docker cp $IMAGE_NAME-tester-$IMAGE_TAG:/usr/app/src/test-reports ./artifacts/
- docker rm -f $IMAGE_NAME-tester-$IMAGE_TAG
```

## 6 |正确标记您的容器

如果您在 CI 管道中构建容器，请确保不要仅仅将它们标记为`latest`。这将有助于部署它们；但这也将确保你可以重新运行管道，而不会破坏东西。

如果你只使用`latest`标签，然后重新运行一个更老的管道，你会不小心替换掉你实际的`latest`镜像；因此，您应该尽可能地使用语义版本控制(例如，在您的发布标签上),否则使用您的分支名称和管道 ID 进行标记。

这样，您可以随时重新运行任何管道，而不会覆盖任何标记，并且可以轻松地引用任何图像。

## 7 |添加集成测试

您的服务可能不是完全独立的，并且会使用其他服务。为了确保这些都一起工作，您可以在您的 CI 管道中编写和运行集成测试。

使用 Docker，您甚至可以旋转多个容器——您的关键依赖项——而无需模仿一切，然后运行 Jest 或更复杂的堆栈，如 Puppeteer 或 Cypress 测试(针对 web 应用程序)。

## 8 |以“快速失败”的方式运行测试

添加到 CI 中的步骤和测试越多，单次运行所需的时间就越长。这几乎总是会导致开发人员提交的频率降低，从而导致 CI 运行的频率降低，从而导致由于大量提交而导致的失败难以确定。

这不应该阻止您添加许多测试来尽可能高效地自动化；但是它应该意味着你以最有效的方式分组和运行你的测试。

您能指定在其他测试失败之前失败的关键测试，或者必须通过的测试吗？如果是这样的话，你应该首先运行它们，这样开发者就能得到快速的反馈。如果这些测试通过了，其他的就可以在之后运行了。

如果您有许多测试，您需要在任何分支、任何提交上运行所有检查和测试吗？或者只在夜间运行其中一些就足够了吗？如果你的代码结构足够好，你能先测试你修改过的模块/服务，然后再测试剩下的吗？

## 9 |将工件导出为 JUnit 文件

尝试使用支持解析测试结果的 JUnit 格式的 CI。直接打开一个合并请求并获得所有测试错误和警告的解析概述要容易得多，而不必打开每个失败的 CI 步骤并滚动控制台输出。好的开发者体验意味着更高的产出！

如今，JUnit 如此普及，以至于大多数工具都可以开箱即用地生成它们，或者只需很少的设置。ESLint、Jest、Cypress 和许多其他工具可以输出 Junit XML 文件；GitLab 等 CI 管道可以解析它们，并自动在 CI 管道分支的合并请求中显示它们。

此外，如果您有额外的 KPI，请尝试将其导出，以便您可以看到它们随时间的变化。例如，如果您重视代码覆盖率，将它传递给您的 CI；或者，如果您关心特性覆盖率，请为您的 CI 计算并传递它。

对于 GitLab，解析 Jest Junit 文件以及代码覆盖率在 CI 步骤中会是这样的:

```
Test:
  script:
    - npm run test # ...
  artifacts:
    name: Test results
    paths:
      - artifacts/
    expire_in: 4 weeks
    reports:
      junit:
        - artifacts/*.xml
  coverage: /All files[^|]*\|[^|]*\s+([\d\.]+)/
```

## 10 |使用您的 CI 进行部署

通过您的 CI 进行部署，以进一步减少出错的空间。它将使您能够重新播放部署以恢复更改(即使您最初没有蓝/绿部署)，它将消除容易出错的手动部署列表，并且一旦设置好，它将大大增加发布信心。

此外，您可以更容易地更新您的文档，而不会忘记任何东西。

假设您使用 Bugsnag 之类的错误报告工具，那么您可以在每次部署后将发布信息推送到 Bugsnag，这样您的错误指示板就可以保持最新。

你有一个`CHANGELOG.md`文件吗？你可以 grep 推送的版本的变化，并在你的团队频道中公布。

**进入专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)