## Chatroom
PHP + Swoole 开发的简单聊天室demo, 主要是 websockt 的应用 。

## 环境要求
* PHP >= 7.0
* Swoole
* composer

## 项目地址
https://github.com/kesixin/Chatroom

## 安装
```
git clone https://github.com/kesixin/Chatroom
composer install
```

## 启动 websockt
```
cd ./webim
php webim_server.php
```

## 启动 PHP 内置服务器
```
cd ./public
php -S localhost:8000
```
浏览器访问 localhost:8000 即可进入聊天

## 截图
![效果图](https://upload-images.jianshu.io/upload_images/6673460-2326bb392428d52f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 项目测试地址
http://test.kesixin.xin/ ，由于没开启端口，可能无法运行，需要请联系！