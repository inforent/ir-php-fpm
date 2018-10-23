FROM php:7.2-fpm

RUN    rm /usr/local/etc/php-fpm.d/*docker* \
    && rm /usr/local/etc/php-fpm.d/www.conf \
    && mkdir  /usr/local/etc/php-fpm.d/inforent.d/ \
    && echo  "[global]\n\
daemonize = no\n\
error_log = /proc/self/fd/2\n\
;for each pool please add\n\
;access.log = /proc/self/fd/2\n\
;catch_workers_output = yes\n\
;place pools unter mapped volume /usr/local/etc/php-fpm.d/inforent.d/\n\
include=etc/php-fpm.d/inforent.d/*.conf\n\
" >/usr/local/etc/php-fpm.d/inforent.conf

RUN apt-get update && apt-get install  -y \
       libfreetype6-dev  \
       libjpeg62-turbo-dev \
       libpng-dev \
       libldap2-dev \
       libgeoip-dev \
       libxslt1-dev \
       libbz2-dev \
       msmtp \
    && docker-php-ext-configure  gd --with-gd \
                                    --with-jpeg-dir \
                                    --with-freetype-dir \
                                    --enable-gd-native-ttf \
    && docker-php-ext-install gd \
    && docker-php-ext-install ldap \
    && docker-php-ext-install gettext \
    && docker-php-ext-install opcache \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install bz2 \
    && docker-php-ext-install xsl \
    && pecl install apcu \
    && pecl install redis \
    && pecl install geoip-1.1.1 

