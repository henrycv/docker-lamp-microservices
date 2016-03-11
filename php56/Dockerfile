FROM php:5.6-fpm

MAINTAINER Yevhenii Dumskyi "yevhenii.dumskyi@gmail.com"

ADD config.ini /etc/php5/fpm/conf.d/
ADD config.ini /etc/php5/cli/conf.d/

RUN apt-get update && apt-get install -my curl wget vim-common mc

# Install composer
RUN bash -c "wget http://getcomposer.org/composer.phar && mv composer.phar /usr/local/bin/composer"
RUN bash -c "chmod 0777 /usr/local/bin/composer"

# install extensions
RUN docker-php-ext-install bcmath mbstring

# Install XDebug
RUN pecl install xdebug-2.3.2
RUN docker-php-ext-enable xdebug

ADD xdebug.ini /usr/local/etc/php/conf.d/

# Need for MC
RUN bash -c "export TERM=xterm"
