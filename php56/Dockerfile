FROM php:5.6-fpm

MAINTAINER Yevhenii Dumskyi "yevhenii.dumskyi@gmail.com"

RUN apt-get update && apt-get install -my \
        curl \
        wget \
        vim-common \
        mc \
        libxml2-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        ssmtp \
    && docker-php-ext-install -j$(nproc) iconv mcrypt bcmath mbstring pdo pdo_mysql soap \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

# Install composer
RUN bash -c "wget http://getcomposer.org/composer.phar && mv composer.phar /usr/local/bin/composer"
RUN bash -c "chmod 0777 /usr/local/bin/composer"

# Install XDebug
RUN pecl install xdebug-2.3.2
RUN docker-php-ext-enable xdebug

ADD xdebug.ini /usr/local/etc/php/conf.d/
ADD config.ini /usr/local/etc/php/conf.d/

RUN cp /etc/ssmtp/ssmtp.conf /etc/ssmtp/ssmtp.conf.bak
COPY ssmtp.conf /etc/ssmtp/ssmtp.conf  

# Need for MC
RUN bash -c "export TERM=xterm"

RUN wget https://files.magerun.net/n98-magerun.phar
RUN chmod 0777 n98-magerun.phar
RUN cp ./n98-magerun.phar /usr/local/bin/n98-magerun

RUN useradd -ms /bin/bash greg
USER greg
