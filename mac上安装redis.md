### 安装redis

通过homebrew安装redis:
`$ brew install redis`

### 启动redis

可以通过以下命令启动redis：
`$ redis-server /usr/local/etc/redis.conf`
终端输出

### 检测redis服务器是否启动

重新打开一个终端窗口，输入命令
`$ redis-cli ping`
该终端输出
`pong`
说明服务器运作正常。

### 关闭redis

在另外一个终端窗口执行`$ redis-cli shutdown`,此时第一个窗口输出