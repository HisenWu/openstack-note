#  kolla项目  
kolla项目是TripleO项目的一部分，聚焦于使用docker容器部署openstack服务。 
项目于2014年9月开始，目前发布了两个release。参与贡献者有约14人。是openstack的孵化项目。

在裸金属上部署openstack不是killo项目当前的目标。因此一个用于部署kolla cluseter的环境是必须的。
当前，使用heat模板在已经存在的openstack cloud上部署一个Kolla cluster。

当前Kolla项目在[Kollaglue repo]提供了以下服务的docker镜像。
<pre><code>$ sudo docker search kollaglue</code></pre>

### 代码目录结构  
+ docker  
    创建docker image  
+ k8s  
    创建kubenetes的pods和service配置文件
+ tools  
    与Kolla交互的各种工具  
+ devenv  
    管理Kolla开发环境的一些工具。

### 当前的问题  
当前升级和降级openstack主要有两种方式，基于image与基于package。  
基于image的方式，更新是原子的。
基于package的更新方式通常不是原子的，升级过程中存在很多导致失败的原因，可能存在部分package更新失败的可能。

### 使用场景
1. 原子性的升级或者回退openstack部署。  
2. 基于组件升级openstack。  
3. 基于组件回退openstack。  

### 安全与其他  
某些容器可能需要privileged，某些可能需要host相同的namespace。 
安全加强可以使用Selinux或者AppArmor。  



[Kollaglue repo]: https://registry.hub.docker.com/repos/kollaglue/
### 参考  
1. https://github.com/stackforge/kolla/blob/master/specs/containerize-openstack.rst  
2. https://github.com/stackforge/kolla  
3. https://github.com/sdake/compute-upgrade
