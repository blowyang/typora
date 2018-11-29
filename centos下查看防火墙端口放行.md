查看所有打开的端口： firewall-cmd --zone=public --list-ports

添加

firewall-cmd --zone=public --add-port=80/tcp --permanent    （--permanent永久生效，没有此参数重启后失效）

重新载入

firewall-cmd --reload

查看

firewall-cmd --zone= public --query-port=80/tcp

删除

firewall-cmd --zone= public --remove-port=80/tcp --permanent

 

批量开放端口

firewall-cmd --permanent --zone=public --add-port=100-500/tcp
firewall-cmd --permanent --zone=public --add-port=100-500/udp
firewall-cmd --reload