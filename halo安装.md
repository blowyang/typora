### 自动打包脚本

> 这种安装方式适用于所有Linux发行版，其中，**deploy.sh**在项目根目录。

####  

#### 注意事项

- 服务器为Linux。
- JDK1.8以上（需要自己配置）。
- Maven3.x（需要自己配置）。
- Git。

####  

#### 拉取源码

```
git clone https://github.com/ruibaby/halo
#或者
git clone https://gitee.com/babyrui/halo
```

####  

#### 如何运行

1. 进入到源码根目录。

2. 修改配置文件，`src/main/resources/application.yaml`，请参考上面的配置文件详解。

3. 执行`sh deploy.sh`。注意执行之前，应该正确修改halo的根目录

   ```
   # 指定Halo的根目录，请按实际修改
   HALO_DIR="/www/wwwroot/halo"
   ```

   

#### 如何更新

1. 进入到源码根目录。
2. 执行`git pull`。
3. 执行`sh deploy.sh`。