使用[<font >acme.sh</font>](https://github.com/acmesh-official/acme.sh)

<font>github链接:</font>

[https://github.com/acmesh-official/acme.sh/wiki/%E8%AF%B4%E6%98%8E](https://github.com/acmesh-official/acme.sh/wiki/%E8%AF%B4%E6%98%8E)

# 安装[<font>acme.sh</font>](https://github.com/acmesh-official/acme.sh)
安装初始化并自动更新

```shell
# my@example.com为注册letsencrypt 的邮箱

curl https://get.acme.sh | sh -s email=my@example.com

#
```

# 生成证书
> tip：建议设置<font>ca服务器改成letsencrypt 防止出现pending</font>
>

```shell
acme.sh --set-default-ca --server letsencrypt
```

1. http方式   
<font style="color:rgb(31, 35, 40);">在你的网站根目录下放置一个文件, 来验证你的域名所有权</font>

```shell
# mydomain.com 要注册的域名
# /app/mydomain.com/ 域名资源根目录

acme.sh --issue -d mydomain.com -d www.mydomain.com --webroot /app/mydomain.com/
```

2. <font style="color:rgb(31, 35, 40);">手动dns  
</font><font style="color:rgb(31, 35, 40);">不会自动更新证书，不建议；详情看文档</font>

# <font style="color:rgb(31, 35, 40);">复制安装证书</font>
+ <font style="color:rgb(31, 35, 40);">Apache example</font>

```shell
# example.com 注册的域名
# /ssl/to/certfile/in/apache/cert.pem 存放的路径以及文件名
# --reloadcmd 重载命令

acme.sh --install-cert -d example.com \
--cert-file      /ssl/to/certfile/in/apache/cert.pem  \
--key-file       /ssl/to/keyfile/in/apache/key.pem  \
--fullchain-file /path/to/fullchain/certfile/apache/fullchain.pem \
--reloadcmd     "service apache2 force-reload"
```

+ <font style="color:rgb(31, 35, 40);">Ngnix example</font>

```shell
# example.com 注册的域名
# /ssl/to/certfile/in/apache/cert.pem 存放的路径以及文件名
# --reloadcmd 重载命令

acme.sh --install-cert -d example.com \
--key-file       /ssl/to/keyfile/in/nginx/key.pem  \
--fullchain-file /ssl/to/fullchain/nginx/cert.pem \
--reloadcmd     "service nginx force-reload"
```

# 更新证书
```shell
crontab  -l

# 类似结果 56 * * * * "/root/.acme.sh"/acme.sh --cron --home "/root/.acme.sh" > /dev/null
```

# <font style="color:rgb(31, 35, 40);">更新acme.sh</font>
+ 手动更新

```shell
acme.sh --upgrade
```

+ 自动更新

```shell
# 开启自动更新
acme.sh --upgrade --auto-upgrade

# 关闭自动更新
acme.sh --upgrade --auto-upgrade  0
```

# 出错
```shell
acme.sh --issue  .....  --debug

#或者

acme.sh --issue  .....  --debug  2
```

