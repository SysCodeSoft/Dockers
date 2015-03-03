FROM debian:7

MAINTAINER Max Trifonov <mp.trifonov@gmail.com>

RUN apt-get update \
    && apt-get install -y \
       ca-certificates \
       curl \
       wget \
       git \
    && echo "deb http://packages.dotdeb.org wheezy all" >> /etc/apt/sources.list \
    && echo "deb-src http://packages.dotdeb.org wheezy all" >> /etc/apt/sources.list \
    && echo "deb http://packages.dotdeb.org wheezy-php56-zts all" >> /etc/apt/sources.list \
    && echo "deb-src http://packages.dotdeb.org wheezy-php56-zts all" >> /etc/apt/sources.list \
    && wget http://www.dotdeb.org/dotdeb.gpg \
    && apt-key add dotdeb.gpg \
    && apt-get update \
    && apt-get clean; \ 

    apt-get install -y \
       nginx \
       php5-cli \
       php5-common \
       php5-sqlite \
       php5-cgi \
       php5-mysqlnd \
       php5-mysqli \
       php5-mongo\
       php5-pgsql\
       php5-curl\
       php5-gd \
       php5-memcached \
       php5-mcrypt \
       php5-imagick \
       php5-fpm \
    && apt-get clean ; \ 
    
    curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer; \
   
    rm /etc/nginx/sites-available/default \
    && rm /etc/nginx/sites-enabled/default

COPY default.conf /etc/nginx/sites-available/default

RUN ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default

