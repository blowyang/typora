### 下载安装文件

`http://httpd.apache.org/`

### 安装

将下载的压缩包解压，得到如下文件目录，并在apache的bin目录下启动命令行，运行httpd -k install，如果有报错，解决完报错之后，运行httpd -k uninstall卸载apache再重新运行httpd -k install。

### 启动

打开cmd，进入Apache下bin目录，运行httpd -k start

回车，则Apache启动成功。可打开任意浏览器，在地址栏输入：localhost  回车，如果出现下图则表明启动成功：

**停止Apache运行**

回到cmd面板，httpd -k stop回车，可在浏览器地址栏中再次输入：localhost 回车，出现如下界面则表明Apache服务关闭：