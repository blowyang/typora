### Apache网站下载JDK

https://tomcat.apache.org/download-90.cgi

执行命令：

wget http://mirror.bit.edu.cn/apache/tomcat/tomcat-9/v9.0.8/bin/apache-tomcat-9.0.8.tar.gz

### 解压tomcat包

执行命令：tar -zxvf apache-tomcat-9.0.8.tar.gz 

### 启动Tomcat

进入bin文件夹，执行如下命令：

./startup.sh

### Tomcat服务器开机自启动

在/etc/init.d目录下新建tomcat文件

```
sudo cd /etc/init.d
sudo vi tomcat
```

添加启动、关闭、重启的shell脚本

```
#!/bin/sh
### BEGIN INIT INFO
# Provides:	        tomcat
# Required-Start:	$remote_fs $network
# Required-Stop:	$remote_fs $network
# Default-Start:	2 3 4 5
# Default-Stop:		0 1 6
# Short Description:	the tomcat Java Application Server
### END INIT INFO
 
RETVAL=0
export CATALINA_BASE=/usr/tomcat8   # xxx为自己的用户名
 
start()
{
	if [ -f $CATALINA_HOME/bin/startup.sh ]
	then
	    echo $"Starting Tomcat"
		$CATALINA_HOME/bin/startup.sh
	    RETVAL=$?
	    echo "OK"
	    return $RETVAL
	fi
}
 
 
stop()
{
	if [ -f $CATALINA_HOME/bin/shutdown.sh ]
	then
	    echo $"Stopping Tomcat"
		$CATALINA_HOME/bin/shutdown.sh
	    RETVAL=$?
	    sleep 3
	    ps -fwwu tomcat | grep apache-tomcat | grep -v grep | grep -v PID | awk '{print $2}'| xargs kill -9
	    echo "OK"
	   return $RETVAL
	fi
}
 
 
case "$1" in
	start)
		start
		;;
	stop)
		stop
		;;
	restart)
		echo $"Restarting Tomcat"
		$0 stop
		sleep 3
		$0 start
		;;
	*)
		echo $"Usage:$0{start|stop|restart}"
		exit 1
		;;
esac
 
exit $RETVAL

```

保存退出，授予tomcat文件执行权限

```
chmod +x tomcat
```

使tomcat服务生效，并使能开机自启动，然后reboot重启，即可Tomcat开机自启动生效.

```
sudo systemctl daemon-reload        #对于新创建的unit文件或修改了的unit文件，要通知systemd重载此配置文件；
sudo systemctl enable tomcat        #使能开机自启动
(sudo systemctl disable tomcat        #取消开机自启动)
sudo reboot
```

重启后，执行systemctl status tomcat看看tomcat服务的状态。



终端启动tomcat

```
systemctl start tomcat
```



### 修改Linux网关

在CentOS 7中引入了一个更强大的防火墙——Firewall。我们需要在Firewall中开启8081端口，也就是将8081端口加入到zone（Firewall的新特性，简单讲它的作用就是定义了网络区域网络连接的可信等级）中。命令如下：

```
firewall-cmd --zone=public --add-port=8080/tcp --permanent
```

这样就成功的将8080端口加入了public区域中，permanent参数表示永久生效，即重启也不会失效，最后不要忘记更新防火墙规则：

firewall-cmd --reload
OK，下面看一下public区域下所有已打开的端口，命令如下：

firewall-cmd --zone=public --list-ports

可以看到8080端口已经成功打开：

### 访问成功-后续HTTPS

现在追加HTTPS：

执行命令生成key，到tomcat的config目录下。

    keytool -genkey -alias tomcat -keyalg RSA -keystore /Data/tomcat/apache-tomcat-9.0.8/conf/.keystore 

https连接需要用到数字证书与数字签名(MD5算法)

网站https连接首先需要申请数字证书，配置加密连接器，浏览器安装证书

使用java的工具keytool产生数字证书,生成文件.keystore.

修改conf/server.xml文件，修改加密连接器，添加keystoreFile与keystorePass：

