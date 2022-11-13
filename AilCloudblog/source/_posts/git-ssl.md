---
title: hexo部署ssl证书
date: 2022-08-25 23:57:48
categories: ['Githube','hexo']
tags: ['Centos','博客']
---

## 部署ssl证书
**保证etc/ssl目录存在,没有的话创建一个ssl目录**
```
mkdir etc/ssl
```
编辑nginx的配置文件
```
vim /usr/local/nginx/conf/nginx.conf
```
调整以下参数或者直接应用配置文件中的模板，依次对照进行修改。
```
http{
    #http节点中可以添加多个server节点
    server{
        #监听443端口
        listen 443;
        
        server_name 你的域名;
        ssl on;
        ssl_certificate /etc/ssl/你的证书.crt.pem;
        ssl_certificate_key /etc/ssl/你得证书.key;
        ssl_session_timeout 5m;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:HIGH:!aNULL:!MD5:!RC4:!DHE;
        ssl_prefer_server_ciphers on;
       
        location / {
                #文件夹
                root /usr/local/service/ROOT;
                #主页文件
                index index.html;
        }
    }
    server{
        listen 80;
        server_name 你的域名;
        rewrite ^/(.*)$ https://你的域名:443/$1 permanent;
    }
}
```
**重新启动nginx即可完成**