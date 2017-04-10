# 介绍

使用docker部署lnmpr（Linux，Nginx，MySQL，PHP7，Redis）。

### 整个环境类似

![readme][1]

整个应用程序分为四个容器

Nginx正在Nginx容器中运行，它处理请求并作出响应。
PHP或PHP-FPM放在PHP-FPM容器中，它从主机检索php脚本，解释，执行然后响应Nginx。如果需要，它也将连接到MySQL。
MySQL在于MySQL集装箱，
Redis在于Redis集装箱，
我们的应用脚本位于主机上，您可以直接编辑文件，而无需重新构建/重新启动整个映像/容器。

### 必要说明

````
1. docker-compose.yml 里面定义了需要使用哪些服务，比如nginx、mysql、php、redis等相关参数，
你可以根据自己的需要进行修改、删除及添加

2. app/src 中的代码为laravel 5.4 源码，开箱即用，如不使用，直接删除即可。

3. 该nginx中为laravel配置做了优化，把运行目录定在了/public目录，如果需要使用该环境
用在非laravel的项目中，请再构建前，修改nginx/conf.d/default.conf中的
root   /usr/share/nginx/html/public; --> root   /usr/share/nginx/html;

4. 本地测试的ssh证书为a.ric.com 证书为自生成的测试证书，如果需要使用，请替换nginx/ca目录中的相关证书文件。
````

### 构建和运行

首先你必须安装了 [Docker](https://docs.docker.com) 和 [Docker Compose](https://docs.docker.com/compose) installed.

然后利用 `docker-compose` 命令一键部署:

    $ sudo docker-compose up

有关docker-compose的使用帮助:

    $ sudo docker-compose --help

然后执行你的 https://\<docker-host\> :beer:

### 基础版本

[micooz/docker-lnmp](https://github.com/micooz/docker-lnmp)


### License

MIT

  [1]: readme.png
