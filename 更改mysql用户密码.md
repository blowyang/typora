### 以root用户进入数据库

`>mysql -u root -p`

### 查看所有用户

select host, user from mysql.user;

### 更改用户名密码

以root用户为例，进行说明

`mysql>UPDATE mysql.user SET authentication_string=PASSWORD('password') WHERE User='root';`

### 刷新MySQL的系统权限相关表

`mysql>flush privileges;`