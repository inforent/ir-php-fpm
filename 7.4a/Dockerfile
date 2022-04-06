FROM php:7.4-fpm

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
       locales \
       libzip-dev \
    && echo "\n\
de_DE ISO-8859-1\n\
de_DE.UTF-8 UTF-8\n\
de_DE@euro ISO-8859-15\n\
en_GB ISO-8859-1\n\
en_GB.ISO-8859-15 ISO-8859-15\n\
en_GB.UTF-8 UTF-8\n\
en_US ISO-8859-1\n\
en_US.ISO-8859-15 ISO-8859-15\n\
en_US.UTF-8 UTF-8\n\
" >> /etc/locale.gen \
    && dpkg-reconfigure --frontend=noninteractive locales

RUN docker-php-ext-configure  gd \
                                 --with-jpeg \
                                 --with-freetype                                 
RUN docker-php-ext-install gd
RUN docker-php-ext-install ldap
RUN docker-php-ext-install gettext
RUN docker-php-ext-install opcache
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install pdo_mysql 

RUN docker-php-ext-install bz2 
RUN docker-php-ext-install xsl 
RUN docker-php-ext-install soap 
RUN docker-php-ext-install zip 
RUN docker-php-ext-install intl
RUN docker-php-ext-install exif
RUN pecl install apcu
RUN pecl install redis
RUN pecl install imagick
