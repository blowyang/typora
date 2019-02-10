## 安装：

1.获取redis资源

　　wget http://download.redis.io/releases/redis-4.0.8.tar.gz

2.解压

　　tar xzvf redis-4.0.8.tar.gz

3.安装

　　cd redis-4.0.8

　　make

　　cd src

　　make install PREFIX=/usr/local/redis

4.移动配置文件到安装目录下

　　cd ../

　　mkdir /usr/local/redis/etc

　　mv redis.conf /usr/local/redis/etc

 5.配置redis为后台启动

　　vi /usr/local/redis/etc/redis.conf //将**daemonize no** 改成daemonize yes

6.将redis加入到开机启动

　　vi /etc/rc.local //在里面添加内容：/usr/local/redis/bin/redis-server /usr/local/redis/etc/redis.conf (意思就是开机调用这段开启redis的命令)

7.开启redis

　　/usr/local/redis/bin/redis-server /usr/local/redis/etc/redis.conf 

 

常用命令　　

　　redis-server /usr/local/redis/etc/redis.conf //启动redis

　　pkill redis  //停止redis

8.配置环境变量

sudo vim  /etc/prifile

在文件中添加

export PATH="/home/blowyang/anaconda3/bin:/usr/local/redis/bin:$PATH"

按【esc】键，输入（:wq）组合字符，保存并退出文件，然后在终端中执行该文件

source /etc/proflie

接下来就可以无路径启动redis

在终端中输入 redis-server,启动服务

在终端中输入 redis-cli，启动客户端

输入ping

系统输出dong，证明成功

## 卸载：

　　　　rm -rf /usr/local/redis //删除安装目录

　　　　rm -rf /usr/bin/redis-* //删除所有redis相关命令脚本

　　　　rm -rf /root/download/redis-4.0.4 //删除redis解压文件夹