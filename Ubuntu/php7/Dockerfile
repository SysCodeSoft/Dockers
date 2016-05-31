FROM ubuntu:16.04

MAINTAINER Max Trifonov <mp.trifonov@gmail.com>

RUN apt-get update \
    && apt-get install -y \
    software-properties-common \
    python-software-properties;

RUN add-apt-repository ppa:ondrej/php-zts \
    &&  apt-get update \
    && apt-get install -y --allow-unauthenticated \
       php7.0-zts \
       php7.0-zts-dev \
       ca-certificates \
       curl \
       wget \
       git \
    && apt-get clean ; \ 
    
    curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer; 

RUN cd /; \
    git clone https://github.com/krakjoe/pthreads.git; \
    cd /pthreads; \
    phpize; \
    ./configure; \
    make -j8; \
    make install; \
    echo "extension=pthreads.so" > pthreads.ini; \
    cp pthreads.ini /etc/php/7.0-zts/cli/conf.d/pthreads.ini;
   
EXPOSE 80
