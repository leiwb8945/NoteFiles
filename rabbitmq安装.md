## ***\*10RabbitMQ之安装\****

第一步  安装elang包(erlang-21.3-1.el7.x86_64.rpm)：

rpm -ivh erlang-21.3-1.el7.x86_64.rpm

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml24012\wps1.jpg) 

第二步  安装依赖包(必须要有网络):

 yum install socat –y

第三步  安装rabbitMq (rabbitmq-server-3.8.8-1.el7.noarch.rpm) 

rpm -ivh rabbitmq-server-3.8.8-1.el7.noarch.rpm

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml24012\wps2.jpg) 

第四步开机启动rabbit MQ 服务：

chkconfig rabbitmq-server on

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml24012\wps3.jpg) 

第五步启动本次rabbit Mq服务：

启动  /sbin/service rabbitmq-server start

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml24012\wps4.jpg) 

关闭  /sbin/service rabbitmq-server stop

查看状态  /sbin/service rabbitmq-server status

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml24012\wps5.jpg) 

 

## ***\*11RabbitMQ之安装Web界面插件\****

RabbitMq service后台管理界面需要安装插件

1 开启 web 管理插件(必须要先stop RabbitMq 服务才可以安装):

 rabbitmq-plugins  enable rabbitmq_management

 

 

安装完成就是可以访问了，默认端口为15672

登录的默认账户名和密码为 guest

Guest登录会提示User can only log in via localhost  说明没有权限，只能通过rabbitMq service 端登录。所以需要创建用户以及赋予权限。

 

 

## ***\*12RabbitMQ之添加用户并设置权限\****

1 添加一个新的用户 创建账号 

rabbitmqctl add_user admin 123 

 

2 设置用户角色

rabbitmqctl set_user_tags admin administrator 

 

admin为用户名称

administrator 为角色名称

 

3 设置用户权限

set_permissions [-p  <vhostpath>]  <user> <conf> <write> <read>

rabbitmqctl set_permissions -p "/" admin ".*" ".*" ".*"

 

 

用户 user_admin 具有/vhost1 这个 virtual host 中所有资源的配置、写、读权限 

 

 

 

4 当前用户和角色 

rabbitmqctl list_users

 

(每一个virtual host 代表一个MQ的库，不同的virtual host里面交换机和队列是不一样的 )

 