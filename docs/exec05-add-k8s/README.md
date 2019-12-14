# 练习 5 - 在流水线中添加Azure Kubernetes Services集群环境，完成k8s部署

在这个实验中，我们将完成针对当前应用的Docker容器化改造，并使用Azure Pipeline完成Docker镜像的构建，并发布到Azure Kubernetes环境中。

## 任务 1 - 在代码库中添加Dockerfile

在GitHub Repo中找到 _demo-assets/demo-dockerfile

![](images/2019-12-14_12-47-04.png)

复制此文件内容，并在repo根目录创建Dockefile文件（注意大小写)，在新建的文件中写入以上复制的Dockerfile内容。

![](images/2019-12-14_12-49-02.png)

提交文件到GitHub Repo中。

## 任务 2 - 创建Docker构建流水线

在 Azure Pipeline 中创建新流水线

![](images/2019-12-14_12-51-17.png)

这次我们使用 classic editor ，即创建一条使用可视化界面编辑的流水线配置

![](images/2019-12-14_12-52-16.png)

在 Select Source 页面中选择 Github 作为代码源，并指定你自己的Github repo

![](images/2019-12-14_12-54-05.png)

在 Select a template 页面中选择 Docker container 模板，点击 **Apply** 按钮

![](images/2019-12-14_12-55-20.png)

在 Build an image 步骤中，配置以下参数

- Azure Subscription : 选择你自己订阅（之前已经授权过，就不用再次授权了）
- Azure Container Registry : 选择之前创建的容器注册表实例
- Include latest tag : 这个需要勾选，确保创建的容器镜像包括latest标签

![](images/2019-12-14_12-57-41.png)

在 Push an image 步骤中，设置以下参数

- Azure Subscription : 选择你自己订阅（之前已经授权过，就不用再次授权了）
- Azure Container Registry : 选择之前创建的容器注册表实例
- Include latest tag : 这个需要勾选，确保创建的容器镜像包括latest标签

![](images/2019-12-14_13-00-30.png)

添加 Publish Build Artifact 步骤，点击 + 并搜索 Publish 关键词，定位到此任务，并点击 **Add** 按钮添加到流水线的最后步骤

![](images/2019-12-14_13-02-02.png)

配置以下参数

-Path to publish : 选择 _demo-assets 目录

![](images/2019-12-14_13-04-20.png)

保存并触发构建

![](images/2019-12-14_13-05-23.png)

## 任务 3 - 更新kube-deploy文件

在Github中找到 _demo-assets/kube-deploy.yml文件，并更新第34行设置

![](images/2019-12-14_13-10-13.png)

将以下配置更新为的ACR中的地址

```
image: azuredevops101.azurecr.io/azuredevops101/calculator:latest
```

更新为

```
image: {你的ACR名字}.azurecr.io/{你的项目名称}/calculator:latest
```

更新完成后，再次触发刚才创建的Docker构建。等待此构建完成后再进行后续步骤。

## 任务 4 - 添加 Azure Kubernetes Service (AKS) 到部署流水线中

在以上构建完成的页面上右上角点击 **Release** 按钮

![](images/2019-12-14_13-16-42.png)

在Select tempalte页面中选择 **Deploy to a Kubernetes Cluster** 模板，并点击 **Apply**

![](images/2019-12-14_13-17-02.png)

在kubectl步骤中的Kubernetes service connection部分点击 **New** 创建一个新的服务链接

![](images/2019-12-14_13-19-51.png)

在出现的 **New service connection** 对话框中配置如下参数

- Azure Subscription: 选择你的订阅
- Cluster: 选择我们之前创建的集群
- Namespace: 选择 default
- Service connection name: 自行决定

![](images/2019-12-14_13-21-58.png)

完成以上配置后，点击 **Save**

在 Kubectl 任务中继续配置如下参数

- Namespace: default
- Command: Apply
- Use Configuration file: 勾选后并选择 _demo-asset/kube-deploy.yml 文件

![](images/2019-12-14_13-32-02.png)

在 Kubectl 任务中继续配置如下参数

- Secrets 配置节中
- Azure Subscription：选择你的订阅
- Azure Container Registry: 选择你的ACR
- Secret name: regcred

![](images/2019-12-14_13-26-55.png)

完成以上设置后，保存并触发此部署。

## 任务 5 - 获取服务地址

通过以下命令获取服务地址

``` shell
## 登录azure 账号
az login
## 获取k8s访问密钥
az aks get-credentials -g {资源组名称} -n {AKS集群名称}
## 获取节点信息，pod信息和服务信息
kubectl get nodes
kubectl get pods
kubectl get services
```

之后一个命令将输出calculator服务的对外服务地址，复制此地址到浏览器即可访问运行在k8s服务中的应用了。
