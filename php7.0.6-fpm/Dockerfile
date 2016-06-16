FROM php:7.0.6-fpm

RUN apt-get update -y
RUN apt-get install -y git nano curl telnet vim wget zip apt-utils

COPY php-custom.ini  /usr/local/etc/php/conf.d/php-custom.ini

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer
