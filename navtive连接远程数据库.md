用navtive连接阿里云服务器（Linux）的数据库时，老是连接不上，并且报10060错误，要通过以下两个步骤解决：

1.先进入linux连接数据库并输入密码：

```
mysql -uroot -p
```

 2.输入以下命令进行授权：

```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '这里写自己数据库的密码' WITH GRANT OPTION;
```

3.刷新权限：

```
FLUSH PRIVILEGES;
```

4.添加了权限之后，还是连接不上数据库。必须给服务器的安全组设置3306端口放行规则

5.然后正常连接。

6.若不能连接，请查看服务器防火墙是否放行3306端口。

查看所有打开的端口： 

```
firewall-cmd --zone=public --list-ports
```

若没有放行3306端口，添加放行

```
firewall-cmd --zone=public --add-port=3306/tcp --permanent    
（--permanent永久生效，没有此参数重启后失效）
```

重新载入

```
firewall-cmd --reload
```

