1.下载nodejs最新的bin包到、usr/local/node

可以在下载页面https://nodejs.org/en/download/中找到下载地址。然后执行指令

wget https://nodejs.org/dist/v10.13.0/node-v10.13.0-linux-x64.tar.xz 
然后就是等着下载完毕。

另外你也可以在你喜欢的任意系统上下载最新的bin包，然后通过FTP上传到CentOS上。

2.解压包

依次执行

xz -d node-v10.13.0-linux-x64.tar.xz
tar -xf node-v10.13.0-linux-x64.tar

4. 部署bin文件

先确认你nodejs的路径，我这里的路径为~/node-v9.3.0-linux-x64/bin。确认后依次执行

ln -s /usr/local/node/node-v10.13.0-linux-x64/bin/node /usr/bin/node
ln -s /usr/local/node/node-v10.13.0-linux-x64/bin/npm /usr/bin/npm

注意ln指令用于创建关联（类似与Windows的快捷方式）必须给全路径，否则可能关联错误。

5.测试

node -v
npm

如果正确输出版本号，则部署OK



wget https://nodejs.org/dist/v10.13.0/node-v10.13.0-linux-x64.tar.xz

xz -d node-v10.13.0-linux-x64.tar.xz

tar -xf node-v10.13.0-linux-x64.tar

ln -s /usr/local/node/node-v10.13.0-linux-x64/bin/node /usr/bin/node
ln -s /usr/local/node/node-v10.13.0-linux-x64/bin/npm /usr/bin/npm

### CentOS 下源码安装 Node.js

1、下载源码，你需要在<https://nodejs.org/en/download/>下载最新的Nodejs版本，本文以v0.10.24为例:

```
cd /usr/local/src/
wget https://nodejs.org/dist/v10.13.0/node-v10.13.0.tar.gz
```

2、解压源码

```
tar -zxvf node-v10.13.0.tar.gz
```

3、 编译安装

```
cd node-v10.13.0
./configure --prefix=/usr/local/node/10.13.0
make
make install
```

4、 配置NODE_HOME，进入profile编辑环境变量

```
vim /etc/profile
```

设置nodejs环境变量，在 **\*export PATH USER LOGNAME MAIL HOSTNAME HISTSIZE HISTCONTROL*** 一行的上面添加如下内容:

```
#set for nodejs
export NODE_HOME=/usr/local/node/10.13.0
export PATH=$NODE_HOME/bin:$PATH
```

:wq保存并退出，编译/etc/profile 使配置生效

```
source /etc/profile
```

验证是否安装配置成功

```
node -v
```

输出 v0.10.24 表示配置成功

npm模块安装路径

```
/usr/local/node/0.10.24/lib/node_modules/
```

**注：**Nodejs 官网提供了编译好的Linux二进制包，你也可以下载下来直接应用。