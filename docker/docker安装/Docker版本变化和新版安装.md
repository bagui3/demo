[Docker版本变化和新版安装](https://www.cnblogs.com/Peter2014/p/7704306.html)

Docker从1.13版本之后采用时间线的方式作为版本号，分为社区版CE和企业版EE。

社区版是免费提供给个人开发者和小型团体使用的，企业版会提供额外的收费服务，比如经过官方测试认证过的基础设施、容器、插件等。

社区版按照stable和edge两种方式发布，每个季度更新stable版本，如17.06，17.09；每个月份更新edge版本，如17.09，17.10。

官方文档：https://docs.docker.com/engine/installation/linux/docker-ce/centos/

```
#1.配置仓库
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
 
#2.可以选择是否开启edge和test仓库
sudo yum-config-manager --enable docker-ce-edge
sudo yum-config-manager --enable docker-ce-test
sudo yum-config-manager --disable docker-ce-edge
sudo yum-config-manager --disable docker-ce-test
 
#3.安装docker-ce
sudo yum install docker-ce     #由于repo中默认只开启stable仓库，故这里安装的是最新稳定版17.09
 
#4.可以查看所有仓库中所有docker版本，并选择特定版本安装
yum list docker-ce --showduplicates | sort -r
 
docker-ce.x86_64            17.09.0.ce-1.el7.centos            docker-ce-stable
docker-ce.x86_64            17.09.0.ce-1.el7.centos            @docker-ce-stable
docker-ce.x86_64            17.06.2.ce-1.el7.centos            docker-ce-stable
docker-ce.x86_64            17.06.1.ce-1.el7.centos            docker-ce-stable
docker-ce.x86_64            17.06.0.ce-1.el7.centos            docker-ce-stable
docker-ce.x86_64            17.03.2.ce-1.el7.centos            docker-ce-stable
docker-ce.x86_64            17.03.1.ce-1.el7.centos            docker-ce-stable
docker-ce.x86_64            17.03.0.ce-1.el7.centos            docker-ce-stable
 
sudo yum install <FQPN>  例如：sudo yum install docker-ce-17.09.0.ce
 
#5.启动并加入开机启动
sudo systemctl start docker
sudo systemctl enable docker
 
#6.关闭docker-daemon
sudo systemctl stop docker
sudo systemctl disable docker
 
#7.docker安装时默认创建了docker用户组，将普通用户加入docker用户组就可以不使用sudo来操作docker
sudo usermod -aG docker peter
#注：添加用户组之后要退出重新登录才会生效
 
#8.运行hello-world镜像来测试是否安装成功
 
docker run hello-world         #本地没有镜像时会自动从docker hub中下载
 
#9.当出现Hello from Docker!即表示安装成功
```