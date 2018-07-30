# web环境部署

## gunicorn安装

`pip install gunicorn`

## gunicorn启动项目

`gunicorn module_name:variable_name`

例：`gunicorn run:app`

例：`gunicorn -b 0.0.0.0:8000 run:app`

可以通过这个ip访问到服务器

## nginx把本地80端口转到其他端口

### 安装nginx

`sudo apt-get install nginx`

### 配置转发

nginx的默认安装路径在/usr/local/nginx下. 

nginx的默认配置在/etc/nginx下.(nginx.conf在这个下面)

### 把80端口指向8080端口

修改nginx.conf#该文件在/etc/nginx

- 注释掉改行:一定要注释掉那一行！！！
- 可以通过软连接配置，不用直接在nginx.conf中配置

```
    #nginx.conf 中 http 段最后会有以下这两句.
    #这样你就可以把已经配置好的各种 server conf 放在 sites-available 里，
    #如果想启用的时候只要复制或者软连接到上面两个文件夹里，想关掉或者更改配置的时候也比较方便.
    #
    #而默认情况下sites-enabled目录下会放一个sites-available/default的软链接,
    #在sites-available/default已经对localhost进行设置, 
    #导致无论你怎么修改nginx.conf对本地端口进行配置都不会生效. 一直报404错误.
    #所以此处要把sites-enabled注掉. 或者把该软链接换掉.
    #
    include /etc/nginx/conf.d/*.conf;
    #include /etc/nginx/sites-enabled/*; 
```

- 在http配置项中增加如下内容:

```
    server {
        listen 80;
        server_name localhost;

        location / {
            proxy_pass http://localhost:8080;
            proxy_redirect off;
            proxy_set_header Host $host;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Real-IP $remote_addr;
        }
    }
```

- 重启nginx

```
    sudo service nginx restart //或者 sudo nginx -s reload1
```

- 然后就可以直接通过localhost/index.htm来访问8080端口的项目了.

**注**：上面的两个localhost要改

我的第一个是127.0.0.1(实际的地址)

第二个是0.0.0.0:8000(代理的地址)(代理的地址会映射到实际的地址)

然后用gunicorn -b 0.0.0.0:8000打开项目

这样从浏览器上访问项目就不用端口号了

## nginx配置静态文件

当有请求访问实际地址的时候，nginx会根据url，根据所要东西的后缀名（如果匹配）就会按照你配置的路径加上url路径组成绝对路径，在你计算机上找到图片



`http {`

`      erver {`

`         location ~* \.(html|css|js|png|jpg|gif|ico)$ {`

`            root  /srv/www;`

`         }`

`      }`

`}`

location指令用来映射请求到本地文件系统，这里我们使用了简单的正则表达式来匹配html、css、js、png、jpg、gif、ico这些为扩展名的请求，注意 location 指令中使用表达式要用 ~ 或者 ~* 符号指明，~表示区分大小写，~* 表示不区分大小写。而 root 指令用来指定文件在服务器上的基路径，这里指定为 /srv/www。

不是太好理解，举个例子，例如客户端发送了一个 GET 请求 http://localhost/images/logo.png，Nginx 接受到该请求后会将该请求分发到匹配的 location 中处理，显然上面我们写的 location 指令可以截获该请求，接下来 nginx 将 request_uri 和 root 拼接成服务器文件系统路径，这里 request_uri 为 /images/logo.png，root 为 /srv/www ，拼接后路径为 /srv/www/images/logo.png ，最后 nginx 将服务器该图片响应给客户端，如果不存在该文件，则返回 404 。

## 注意

 如果修改了nginx.conf一定要记得重新启动nginx

`sudo service nginx restart `

如果报错，多半是你配置的语法有错，或者是你配置的内容不对

## 总结

最后，总结下这几个部分的关系：

(nginx收到客户端发来的请求，根据nginx中配置的路由，将其转发给WSGI)
nginx：”WSGI，找你的来了！”
(WSGI服务器根据WSGI协议解析请求，配置好环境变量，调用start_response方法呼叫flask框架)
WSGI服务器：”flask,快来接客，客户资料我都给你准备好了！”
(flask根据env环境变量，请求参数和路径找到对应处理函数，生成html)
flask：”!@#$%^……WSGI，html文档弄好了，拿去吧。”
(WSGI拿到html，再组装根据env变量组装成一个http响应，发送给nginx)
WSGI服务器：”nginx,刚才谁找我来着？回他个话，!@#$%^…..”
(nginx再将响应发送给客户端)

### 问题

nginx映射？具体那个实在服务器哪个是在客户端？。。。。。具体流程

```
端口映射就是将主机的IP地址的一个端口映射到局域网中一台机器，当用户访问这个IP的这个端口时，服务器自动将请求映射到对应局域网分机 （就这么简单）
```

当我用gunicorn打开一个项目时，哪里的用户可以访问(局域网里的用户可以访问)