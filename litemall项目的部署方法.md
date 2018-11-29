### nginx反向代理spring-boot项目配置

查看ngnix安装位置

ps -ef | gref nginx

将证书上传到/www/cert文件夹下，证书在～/Desktop/cert

scp -r ~/Desktop/cert/ root@120.27.219.39:/www

修改/www/server/nginx/conf/nginx.conf文件

server {
​    listen 443;
​    server_name ylnet.vip;
​    ssl on;
​    ssl_certificate  /www/cert/1553208_www.ylnet.vip.pem;
​    ssl_certificate_key /www/cert/1553208_www.ylnet.vip.key;
​    ssl_session_timeout 5m;
​    ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
​    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
​    ssl_prefer_server_ciphers on;
​        location / {
​            proxy_set_header X-Real-IP $remote_addr;
​            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
​            proxy_set_header Host $http_host;
​            proxy_set_header X-NginX-Proxy true;
​            proxy_pass http://www.ylnet.vip:8080/;
​            proxy_redirect off;
​        }
}
server {
​    listen 80;
​    server_name ylnet.vip;
​    rewrite ^(.*)$ https://$host$1 permanent;
​        location / {
​            proxy_pass http://www.ylnet.vip:8080;
​            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
​            proxy_set_header X-Forwarded-Proto $scheme;
​            proxy_set_header X-Forwarded-Port $server_port;

        }  

}