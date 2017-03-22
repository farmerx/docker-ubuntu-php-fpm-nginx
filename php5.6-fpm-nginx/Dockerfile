FROM ubuntu:latest

MAINTAINER farmerx "farmerx@gmail.com"

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update
RUN apt-get install -y vim wget curl openssh-server
RUN mkdir /var/run/sshd

# 将sshd的UsePAM参数设置成no
RUN sed -i 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config

RUN echo "root:123456" | chpasswd

RUN apt-get install -y supervisor
RUN mkdir -p /var/log/supervisor

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

EXPOSE 22

# 安装python 扩展
RUN apt-get install -y python-software-properties 
RUN apt-get install -y software-properties-common 

# 添加nginx1.10.1
RUN apt-get install -y nginx 

CMD ["/usr/bin/supervisord"]

# 添加php7.0
#RUN apt-get install -y php
#RUN apt-get install -y php7.0-gd
#RUN apt-get install -y php7.0-mysql
#RUN apt-get install -y php7.0-pgsql


RUN add-apt-repository ppa:zanfur/php5.6 -y
RUN apt-get update
RUN add-get install php5.6 -y
RUN apt-get install php5.6-mysql -y
RUN apt-get install php5.6-pgsql -y 
RUN apt-get install php5.6-curl -y
RUN apt-get install php5.6-gd -y
RUN apt-get install php5.6-fpm -y

# 配置文件修改

RUN ["mkdir","-p","/run/php"]
RUN ["touch","/run/php/php5.6-fpm.sock"]
RUN ["chmod","0777","/run/php/php5.6-fpm.sock"]

COPY nginx.conf /etc/nginx/nginx.conf
COPY default /etc/nginx/sites-available/default

EXPOSE 8080

RUN apt-get install -y net-tools 
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

















