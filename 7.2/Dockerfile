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
       locales \
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
    && dpkg-reconfigure --frontend=noninteractive locales \
    && docker-php-ext-configure  gd --with-gd \
                                    --with-jpeg-dir \
                                    --with-freetype-dir \
    && docker-php-ext-install gd \
    && docker-php-ext-install ldap \
    && docker-php-ext-install gettext \
    && docker-php-ext-install opcache \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install bz2 \
    && docker-php-ext-install xsl \
    && docker-php-ext-install soap \
    && docker-php-ext-install zip \
    && docker-php-ext-install intl \
    && pecl install apcu \
    && pecl install redis \
    && pecl install geoip-1.1.1 

