FROM php:5.5.36-fpm

RUN apt-get update -y
RUN apt-get install -y git nano curl telnet vim wget zip apt-utils

COPY php-custom.ini  /usr/local/etc/php/conf.d/php-custom.ini

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

# SSH
RUN apt-get install -y openssh-server  && \
mkdir /var/run/sshd && \
echo 'root:root' | chpasswd && \
sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd && \
echo "export VISIBLE=now" >> /etc/profile

CMD /usr/sbin/sshd -D
EXPOSE 22
# SSH


