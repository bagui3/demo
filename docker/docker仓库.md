[CentOS 7 : Docker私有仓库搭建和使用](https://blog.csdn.net/fgf00/article/details/52040492)

## 安装并启动docker
```
yum -y install docker
systemctl start docker
systemctl enable docker
```

```
systemctl restart docker #重启
```

## 搭建私有仓库
```
docker pull registry
```
下载完之后我们通过该镜像启动一个容器
```
docker run -d -p 5000:5000 --privileged=true -v /opt/registry:/tmp/registry registry
```
参数说明：  
-v /opt/registry:/tmp/registry :默认情况下，会将仓库存放于容器内的/tmp/registry目录下，指定本地目录挂载到容器
 
–privileged=true ：CentOS7中的安全模块selinux把权限禁掉了，参数给容器加特权，不加上传镜像会报权限错误(OSError: [Errno 13] Permission denied: ‘/tmp/registry/repositories/liibrary’)或者（Received unexpected HTTP status: 500 Internal Server Error）错误

### 2.0?
```
docker run -d -v /home/hzq/registry:/var/lib/registry -p 5000:5000 --restart=always --privileged=true --name registry registry:latest
```
参数说明：  
-v /home/hzq/registry:/var/lib/registry 默认情况下，会将仓库存放于容器内的/var/lib/registry目录下，指定本地目录挂载到容器。

-p 5000:5000 端口映射

--restart=always1 在容器退出时总是重启容器,主要应用在生产环境

--privileged=true 在CentOS7中的安全模块selinux把权限禁掉了，参数给容器加特权，不加上传镜像会报权限错误OSError: [Errno 13] Permission denied: ‘/tmp/registry/repositories/liibrary’)或者（Received unexpected HTTP status: 500 Internal Server Error）错误

--name registry 指定容器的名称


## 客户端上传镜像
修改/etc/sysconfig/docker（Ubuntu下配置文件地址为：/etc/init/docker.conf），增加启动选项(已有参数的在后面追加)，之后重启docker，不添加报错，https证书问题。
```
OPTIONS='--insecure-registry 192.168.0.179:5000'    #CentOS 7系统
other_args='--insecure-registry 192.168.0.179:5000' #CentOS 6系统
```
因为Docker从1.3.X之后，与docker registry交互默认使用的是https，而此处搭建的私有仓库只提供http服务 
在docker公共仓库下载一个镜像
```
docker pull docker.io/centos
```
来修改一下该镜像的tag
```
docker tag centos 192.168.0.179:5000/centos
```
把打了tag的镜像上传到私有仓库
```
docker push 192.168.0.179:5000/centos
```
客户端添加私有仓库地址
```
# 添加这一行
ADD_REGISTRY='--add-registry 192.168.0.179:5000'
```
加上后，search镜像，私有仓库和docker hub上都会显示； 
不加搜索私有仓库，需要命令中指定私有仓库ip

## 使用仓库中的镜像
查询私有仓库中的所有镜像，使用docker search命令：
```
curl -u myuser https://registry_ip:5000/v1/search
curl registry_ip:5000/v1/search
```
```
docker search registry_ip:5000/     #centos 7
docker search registry_ip:5000/library #centos 6
```
查询仓库中指定账户下的镜像，则使用如下命令：
```
docker search registry_ip:5000/account/
```