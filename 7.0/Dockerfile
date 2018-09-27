FROM php:7.2-fpm

ADD https://github.com/inforent/ir-php-fpm/raw/master/files-to-add.tgz /tmp/
RUN cd /tmp &&  tar xzf /tmp/files-to-add.tgz && rm /tmp/files-to-add.tgz && \
    mkdir  /usr/local/etc/php-fpm.d/inforent.d/ && \
    echo "include=etc/php-fpm.d/inforent.d/*.conf" > /usr/local/etc/php-fpm.d/inforent.conf && \
    apt-get update && apt-get install  -y \
       libfreetype6-dev  \
       libjpeg62-turbo-dev \
       libpng-dev \
       alien \
       libldap2-dev \
       libgeoip-dev \
       libxslt1-dev \
       libbz2-dev \
       msmtp \
    && docker-php-ext-install gd \
    && docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu \
    && docker-php-ext-install ldap \
    && docker-php-ext-install gettext \
    && docker-php-ext-install opcache \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install bz2 \
    && docker-php-ext-install xsl \
    && alien -i /tmp/oracle-instantclient*basic*.rpm \
    && alien -i /tmp/oracle-instantclient*devel*.rpm \
    && alien -i /tmp/oracle-instantclient*sqlplus*.rpm \
    && pecl install apcu \
    && pecl install redis \
    && pecl install oci8 \
    && pecl install geoip-1.1.1 

RUN rm -f /tmp/ora*.rpm
