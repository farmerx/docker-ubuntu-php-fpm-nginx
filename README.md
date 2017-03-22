# Dockerfile for PHP based services

This is the Dockerfile which enables building the base Docker image
to be used by php services.

## Building

```
docker build -t php56-fpm-nginx:latest .

```

## Versions

### php version (php -v)
```
PHP 5.6.9 (cli) (built: May 15 2015 09:31:38)
Copyright (c) 1997-2015 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2015 Zend Technologies
```
### nginx version (nginx -v)
```
nginx version: nginx/1.10.1
```  
### php-fpm verison (php-fpm -v)
```
PHP 5.6.9 (fpm-fcgi) (built: May 15 2015 09:32:11)
Copyright (c) 1997-2015 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2015 Zend Technologies
```

## docker run
-v 挂在本地磁盘到docker，下面是我个人的启动方式，进攻参考：
```
docker run --name skylar -p 22222:22 -p 8080:8080 -v C:/Users/bibinbin.INTRA/Documents/skylar_web_code/new_www:/var/www/html -v D:/docker/php/log:/var/log/nginx/ -P -d php-nginx:latest
```





