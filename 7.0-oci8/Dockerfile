FROM inforent/ir-php-fpm:7.0

ADD https://github.com/inforent/ir-php-fpm/raw/master/files-to-add.tgz /tmp/
RUN cd /tmp &&  tar xzf /tmp/files-to-add.tgz && rm /tmp/files-to-add.tgz && \
    apt-get update && apt-get install  -y \
       alien \
       libaio1 \
    && pecl install oci8 

ENV LD_LIBRARY_PATH /usr/lib/oracle/12.2/client64/lib 

RUN rm -f /tmp/ora*.rpm
