

```shell
#安装依赖
yum install build-essential openssl openssl-devel unixODBC unixODBC-devel make gcc gcc-c++ kernel-devel m4 ncurses-devel tk tc

# 1. Erlang安装 /usr/local/erlang
./configure --prefix=/usr/local/erlang
make && make install

vim /etc/profile
export PATH=$PATH:/home/bfpuser/server/erlang/bin
source /etc/profile

#测试是否成功
 cd /home/bfpuser/server/erlang/bin
 ./erl
 ctrl+c 再按 a 退出控制台
 
# MQ /home/bfpuser/server/rabbitmq

xz -d rabbitmq-server-generic-unix-3.7.18.tar.xz
tar -xf rabbitmq-server-generic-unix-3.7.18.tar
mv rabbitmq_server-3.7.18 rabbitmq

启动：rabbitmq-server -detached
关闭：rabbitmqctl stop
查看状态：rabbitmqctl status
 
# 启动插件
rabbitmq-plugins enable rabbitmq_management
rabbitmq-plugins enable rabbitmq_delayed_message_exchange

# 添加账号
rabbitmqctl add_user gouhua rabbitmq_gouhua
# 添加权限 
rabbitmqctl set_permissions -p / gouhua ".*" ".*" ".*" 
# 修改用户角色,将用户设为管理员
rabbitmqctl set_user_tags gouhua administrator 

vim /etc/profile
export PATH=$PATH:/home/bfpuser/server/rabbitmq/sbin
source /etc/profile

```
