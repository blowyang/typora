li@Lenovo-B470:/usr/lib/tomcat/apache-tomcat-7.0.55/bin$ sh startup.shUsing 

CATALINA_BASE:   /usr/lib/tomcat/apache-tomcat-7.0.55
Using CATALINA_HOME:   

/usr/lib/tomcat/apache-tomcat-7.0.55
Using CATALINA_TMPDIR: 

/usr/lib/tomcat/apache-tomcat-7.0.55/temp
Using JRE_HOME:        

/usr/lib/java/jdk1.7.0_71/jre
Using CLASSPATH:       /usr/lib/tomcat/apache-

tomcat-7.0.55/bin/bootstrap.jar:/usr/lib/tomcat/apache-tomcat-7.0.55/bin/tomcat-

juli.jar
touch: 无法创建"/usr/lib/tomcat/apache-tomcat-7.0.55/logs/catalina.out": 

没有那个文件或目录
./catalina.sh: 385: ./catalina.sh: cannot create 

/usr/lib/tomcat/apache-tomcat-7.0.55/logs/catalina.out: Directory nonexistent

原因:
由于是在普通用户下安装tomcat,linux对/usr/lib目录和/usr/local目录进行了严格的权限设

置，更改掉就好了。

执行

sudo chmod -R 777 /usr/lib/tomcat/
之后,tomcat启动正常

。