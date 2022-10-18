# 绑定资源

资源（Resource）泛指 DCE 平台上通过各个子模块创建的资源，是完成授权的具体数据。
通常资源描述一个或多个操作对象，每个子模块（例如容器管理、服务网格、微服务引擎等）拥有其各自的资源和对应的资源定义详情，如集群、Namesapce、网关等。

资源的拥有者是主账号 Super Admin，他具有在各子模块创建/管理/删除资源的权限。
普通用户在没有授权的情况下，不会自动拥有资源的访问权限，需要资源拥有者授权。
通常资源拥有者将一组资源加入到某个工作空间，再通过工作空间给用户（用户组）授权是常规操作流程。

资源处于工作空间层次结构的最低级层级，资源包括集群、Namespace、网关等。
所有这些较低层级资源的父级只能是工作空间，而工作空间作为资源容器，是一种资源分组单位。
工作空间通常用于指代一个项目或环境，每个工作空间中的资源相对于其他工作空间中的资源是物理隔离的。
您可以通过工作空间中的授权，授予 IAM 用户（用户组）同一组资源的不同访问权限。