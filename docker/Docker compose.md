###安装 Compose
运行下边的命令来安装 Compose：

```
curl -L https://github.com/docker/compose/releases/download/1.3.1/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```
注意：如果你在安装的时候出现了 “Permission denied” 的错误信息，这说明你的 /usr/local/bin 目录是不可写的，你需要使用超级用户来安装。运行 sudo -i , 然后运行上边的两个命令，然后 exit 退出。

可选，你也可以在 shell 中使用命令行安装。

Compose 适用于 OS X 和 64位的Linux 。 如果你使用其他平台，你可以安装一个 Compose 的 Python 包来完成安装。

```
$ sudo pip install -U docker-compose
```
到这里安装就结束了；Compose已经安装完成。你可以使用 docker-compose --version 来进行测试 。