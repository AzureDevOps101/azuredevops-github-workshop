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