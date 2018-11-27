## Windows安装maven

新建系统变量 **MAVEN_HOME**，变量值：D:\apache-maven-3.6.0



## Linux服务器安装maven

### 创建maven的文件夹并下载maven的tar包到此文件夹中

```
//进入一个目录
cd /usr/local
//创建一个文件夹
mkdir maven
cd maven
//下载maven的tar包
wget http://mirrors.hust.edu.cn/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
//解压tar包
tar -xvf apache-maven-3.6.0-bin.tar.gz
```

### 配置环境变量

```
//打开环境变量的配置文件
vim /etc/profile
```

```
//新增行MAVEN_HOME,等于号后面是maven解压的文件夹地址
MAVEN_HOME=/usr/local/maven/apache-maven-3.6.0
//找到PATH行,追加$MAVEN_HOME/bin
例如
PATH=$JAVA_HOME/bin:$MAVEN_HOME/bin:$PATH
export MAVEN_HOME PATH
```

退出esc，在终端输入：wq，意思是保存并退出

```
//重新刷新配置文件
source /etc/profile
```