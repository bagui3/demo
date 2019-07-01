本地连接 
mysql -u 用户名 -p 密码 
远程连接 
mysql -h 远程ip或域名 -p 端口 -u 用户名 -p 密码


创建用户：
CREATE USER 'username'@'host' IDENTIFIED BY 'password';

username – 你将创建的用户名说明:

host – 指定该用户在哪个主机上可以登陆,如果是本地用户可用localhost,  如 果想让该用户可以从任意远程主机登陆,可以使用通配符%

password –  该用户的登陆密码,密码可以为空,如果为空则该用户可以不需要密码登 陆服务器

授权
GRANT privileges ON databasename.tablename TO 'username'@'host';

privileges – 用户的操作权限,如SELECT , INSERT , UPDATE  等(详细列表见该文最后面).如果要授予所 的权限则使用ALL说明: 

databasename –  数据库名

tablename-表名,如果要授予该用户对所有数据库和表的相应操作权限则可用* 表示, 如*.*

创建数据库
CREATE DATABASE 数据库名;