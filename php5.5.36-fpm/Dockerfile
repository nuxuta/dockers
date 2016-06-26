FROM php:5.5.36-fpm

RUN apt-get update -y
RUN apt-get install -y git nano curl telnet vim wget zip apt-utils

RUN cd /usr/src/php/ext && wget -q https://github.com/xdebug/xdebug/archive/XDEBUG_2_4_0.zip && unzip XDEBUG_2_4_0.zip
RUN docker-php-ext-install xdebug-XDEBUG_2_4_0

RUN apt-get install libpq-dev -y
RUN pecl install apcu
RUN docker-php-ext-install opcache
RUN docker-php-ext-install pdo_pgsql
RUN docker-php-ext-install zip
RUN docker-php-ext-install json
RUN docker-php-ext-install bcmath
RUN docker-php-ext-install pcntl
RUN docker-php-ext-install sockets

COPY php-custom.ini /usr/local/etc/php/conf.d/php-custom.ini
COPY ext-xdebug.ini /usr/local/etc/php/conf.d/ext-xdebug.ini
COPY ext-apcu.ini /usr/local/etc/php/conf.d/ext-apcu.ini

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

# SSH
RUN apt-get install -y openssh-server && \
mkdir /var/run/sshd && \
echo 'root:root' | chpasswd && \
sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd && \
echo "export VISIBLE=now" >> /etc/profile

CMD /usr/sbin/sshd -D
EXPOSE 22
# SSH


