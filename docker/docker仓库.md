[CentOS 7 : Docker私有仓库搭建和使用](https://blog.csdn.net/fgf00/article/details/52040492)

## 安装并启动docker
```
yum -y install docker
systemctl start docker
systemctl enable docker
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