FROM php:7.0-fpm

RUN mkdir  /usr/local/etc/php-fpm.d/inforent.d/ && \
    echo "include=etc/php-fpm.d/inforent.d/*.conf" > /usr/local/etc/php-fpm.d/inforent.conf && \
    apt-get update && apt-get install  -y \
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
    && docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu \
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

