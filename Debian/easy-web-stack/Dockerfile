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
       php5-cgi \
       php5-mysqli \
       php5-curl\
       php5-mcrypt \
       php5-fpm \
    && apt-get clean ; \ 
    
    curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer; \
   
    rm /etc/nginx/sites-available/default \
    && rm /etc/nginx/sites-enabled/default

COPY default.conf /etc/nginx/sites-available/default
COPY entrypoint.sh /

RUN ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default \
    && chmod 0777 /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 80
