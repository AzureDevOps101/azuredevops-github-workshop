# DevOps Meetup Workshop

参加了这么多DevOps活动，还是不知道流水线怎么搭建，云环境如何部署，基础设施即代码怎么玩，Docker和Kubernetes也只是别人碗里的巧克力 ... ... 没关系，来参加我们的DevOps Meetup。来自leansoftX.com的徐磊老师既能上台讲理论，也能下台撸代码，既可以陪你聊敏捷，也能和你调试微服务集群。本次分享，徐磊老师讲带领各位小伙伴一起体验一下使用微软近20年实践经验和客户场景磨练出来的成熟DevOps平台所带来的顺滑体验，我们将从一个GitHub上的开源代码仓库开始，一步一步完成持续集成和单元测试，并使用基础设施即代码的方式部署到Azure云环境中的Kubernetes集群环境；然后我们将搭建电子看板，在生产环境发现Bug，使用电子看板追踪Bug的状态，最终修复Bug完成线上环境的修复。你只需要携带笔记本电脑即可，没有变成经验要求，无需DevOps专业知识，你也一样可以搭建流水线玩转微服务。

## 活动日程

本次workshop为动手实验，请自行携带笔记本并准备好个人熟悉的代码编辑器，我们将完成以下操作

- 从讲师提供的GitHub仓库Fork示例代码
- 克隆代码到本地环境，并尝试进行本地开发调试（可选）
- 从GitHub Marketplace启动Azure Pipeline流水线的配置，使用Pipeline as code的方式完成流水线搭建
- 触发流水线执行
- 在Azure云环境中创建App Service作为我们的测试环境，并利用Azure Pipeline内置的部署原子操作完成自动化部署
- 在Azure云环境中创建Azure Kubernetes Service集群环境作为生产环境，并利用Auzre Pipeline完成k8s部署
- 在测试环境和生产环境之间添加审批和质量门禁动作，确保我们的服务可以可靠的发布上线
- 在生产环境中发现问题，并启用Azure Board电子看板功能，创建bug并开始过程追踪
- 添加单元测试，定位Bug，并通过GitHub Pull Request完成代码评审和测试版本部署
- 通过Azure Pipeline完成新版本上线部署

## 操作手册

我们将按照以下练习推进，每个练习都将由讲师先进行操作，然后给与学员15-20分钟的时候实际操作；如果现场无法完成也没有关系，大家可以回去以后自己多操作熟悉几次。本文档会一致在线免费提供给大家。

前提条件

请确保你已经准备了如下环境

- 可用的Github个人账号 <https://www.github.com>
- 可用的Azure DevOps个人账号 <https://dev.azure.com>
- 可用的Azure云控制台账号（需要与以上Azure DevOps使用同一个微软账号）<https://azure.com/free>
- Windows 10/MacOS操作系统环境，推荐更新到最新版本
- 命令行工具
  - cmder for Windows <https://cmder.net/>
  - iTerm2 for MacOS <https://iterm2.com/>
  - Azure CLI <https://docs.azure.cn/zh-cn/cli/>
  - kubectl <https://kubernetes.io/docs/tasks/tools/install-kubectl/>
- 本地调试环境（可选）- 以下实验可以无需进行本地就可以进行，以下环境为可选安装
  - Visual Studio Code <https://code.visualstudio.com/>
  - Git <https://git-scm.com/>
  - Node.js <https://nodejs.org/> 请使用LTS版本


练习列表

- [练习 1 - 准备环境](docs/exec01-env-prep/README.md)
- [练习 2 - 本地调试代码（可选）](docs/exec02-local-debugging/README.md)
- 练习 3 - 搭建Azure Pipeline流水线持续集成部分并触发CI
- 练习 4 - 搭建Azure Pipeline流水线持续部署部分并触发CD
- 练习 5 - 在流水线中添加Azure Kubernetes Services集群环境，完成k8s部署
- 练习 6 - 在生产环境中发现问题，并使用Azure Board电子看板跟踪bug
- 练习 7 - 采用TDD方式完成Bug修复
