## Windows下安装jdk

JAVA_HOME =C:\Program Files\Java\jdk1.8.0_151

path=%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin

## Linux下安装jdk

### 将源文件移动到指定地方

```
mv ~/jdk-8u191-linux-x64.tar.gz /usr/local/java
```

### 解压缩

```
tar -xzvf jdk-8u191-linux-x64.tar.gz
```

### 配置环境

使用过如下指令进入全局环境变量配置,vim是通过vim编辑器进行配置,记住如下几个指令就够了.

  i 为进入编辑模式

 esc是退出编辑然后进行命令模式 

 :wq 为退出加保存

```
vim /etc/profile 
```

然后在最下面进行如下设置,其中 jdk需要改成自己对应的版本

```
#set java enviroment 
JAVA_HOME=/usr/local/java/jdk1.8.0_191
JRE_HOME=/usr/local/java/jdk1.8.0_191/jre
CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH
```



设置完成后,退出vim,然后继续输入如下指令,刷新环境变量

```
source /etc/profile
```