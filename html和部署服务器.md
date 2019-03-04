# html和部署服务器
## html：
整体框架  
```
<html>
    <head>
        <meta charset="utf-8">
        <title>
        </title>
    </head>
    <body>
    </body>
</html>
```
head标签
```  
<head>
<title>网站标题，显示在浏览器上方</title>
</head>
```
h标签
```
<h1>一级标题</h1>
<h2>二级标题</h2>
......
<h6>
```
p标签
```
<p>文字段落</p>
```
div标签
```
<div>
内容块
</div>
```
hr标签
```
<hr>分隔线
```
table标签
表格th为横坐标td为内容
```
<table>
                <tr>
                    <th>作品名称</th>
                    <th>出版信息</th>
                    <th>作品名称</th>
                    <th>初版信息</th>
                </tr>
                <tr>
                    <td>《坟》</td>
                    <td>1927年3月，未名社</td>
                    <td>《热风》</td>
                    <td>1925年11月，北京北新书局</td>
                </tr>
                <tr>
                    <td>《华盖集》</td>
                    <td>1926年8月，北京北新书局</td>
                    <td>《而已集》</td>
                    <td>1928年10月，上海北新书局</td>
                </tr>
            </table>
```
a标签
```
<a href="url">描述</a>
```

## 服务器部署
1. 按量申请最小实例，腾讯云s1，普通硬盘，0.06元/h，公网ip
2. 安装包管理工具yum
```
sudo yum install yum-utils
```
3. 配置yum  
`cd /etc/yum.repos.d/`
新建nginx.repo
```
vi nginx.repo
内容
[nginx-stable]
name=nginx stable repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=1
enabled=1
gpgkey=https://nginx.org/keys/nginx_signing.key
[nginx-mainline]
name=nginx mainline repo
baseurl=http://nginx.org/packages/mainline/centos/$releasever/$basearch/
gpgcheck=1
enabled=0
gpgkey=https://nginx.org/keys/nginx_signing.key
退出操作
1. esc
2. ：wq
```
4. 安装nginx
`sudo yum install nginx`
5. 启动nginx
`nginx -c /etc/nginx/nginx.conf`
6. 浏览器访问公网ip可看到nginx信息
7. 映射html目录
```
vi /etc/nginx/conf.d/default.conf
更改为
server{
    listen 80;
    server_name localhost;
    #charset koi8-r;
    #access_log /var/log/nginx/host.access.log main;
    #location / {
    # root /usr/share/nginx/html;
    # index index.html index.htm;
    #}
    location / {
        root /data/www;
    }
    #error_page 404 /404.html;
    # redirect server error pages to the static page /50x.html
    #
    error_page 500 502 503 504 /50x.html;
    location = /50x.html {
        root /usr/share/nginx/html;
    }
    # proxy the PHP scripts to Apache listening on 127.0.0.1:80
    #
    #location ~ \.php$ {
    # proxy_pass http://127.0.0.1;
    #}
    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    #location ~ \.php$ {
    # root html;
    # fastcgi_pass 127.0.0.1:9000;
    # fastcgi_index index.php;
    # fastcgi_param SCRIPT_FILENAME /scripts$fastcgi_script_name;
    # include fastcgi_params;
    #}
    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    # deny all;
    #}
}
```
8. 服务器新建文件映射的目录
`mkdir 文件名`
9. 发送文件到服务器
```
scp 要发送文件的本地地址 root@公网ip:服务器文件地址
scp C:\Users\zf888\Desktop\source\html\index.html root@152.136.67.5:/data/www/index.html
```
10. 重新加载配置文件
`nginx -s reload`
11. 重新访问公网ip