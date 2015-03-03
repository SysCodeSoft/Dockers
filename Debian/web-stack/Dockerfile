FROM syscode/easy-web-stack 

RUN apt-get update \
    && apt-get install -y \
       php5-sqlite \
       php5-mysqlnd \
       php5-mongo\
       php5-pgsql\
       php5-gd \
       php5-memcached \
       php5-imagick \
    && apt-get clean 
    
