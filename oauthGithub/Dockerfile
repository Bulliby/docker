FROM php:7.1-apache

RUN apt-get update && apt-get install -y git

WORKDIR /var/www

RUN git clone https://github.com/Bulliby/oauthGithub.git
WORKDIR /var/www/oauthGithub

COPY vhost /etc/apache2/sites-enabled/000-default.conf

RUN curl --silent --show-error https://getcomposer.org/installer | php

RUN apt-get install -y zip unzip
RUN php composer.phar install

EXPOSE 80
