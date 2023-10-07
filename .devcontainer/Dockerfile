FROM ubuntu:22.04
ARG DEBIAN_FRONTEND=noninteractive
RUN echo 'start build'
RUN LC_ALL=C.UTF-8
# speed up build in China
RUN sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
RUN apt update
RUN apt install iputils-ping git curl apache2 -y
RUN apt install php composer php-gd php-xdebug php-dev php-redis php-bcmath php-curl php-xml php-readline php-common php-curl php-mysql php-pdo-mysql php-mbstring php-intl php-gmp php-zip -y

RUN a2enmod ssl rewrite lbmethod_byrequests deflate expires proxy proxy_balancer proxy_connect proxy_ftp proxy_http
RUN echo 'start build'
RUN LC_ALL=C.UTF-8
RUN echo '[XDebug]' >> /etc/php/8.1/apache2/php.ini && echo 'xdebug.mode = debug' >> /etc/php/8.1/apache2/php.ini && echo "xdebug.start_with_request = yes" >> /etc/php/8.1/apache2/php.ini

EXPOSE 80
# 前台执行apache2
ENTRYPOINT apachectl -D FOREGROUND
