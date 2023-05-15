+++
title = "nginx 反向代理教程 将ip+端口改为域名访问"
+++
宝塔界面
发送域名 为自定义域名
url 为ip + 端口
ssl 可以用宝塔自带的

```
server {
        server_name blog.everr.xyz; # 替换成自己的域名
        listen       80 ;
        location / {
                proxy_pass http://172.17.0.3:1234;  #这个ip，端口替换成你自己的
                proxy_redirect off;
                proxy_set_header        Host    $host;
                proxy_set_header        X-Real-IP       $remote_addr;
                proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;   
        }
}
```
