FROM waxer/php

RUN pacman -Syyu --noconfirm php-intl git composer

WORKDIR /home/www-owner

RUN curl -o symfony.tar.gz -L --max-redirs 1 https://github.com/symfony-cli/symfony-cli/releases/download/v5.4.11/symfony-cli_linux_amd64.tar.gz

RUN tar -xf symfony.tar.gz && rm -f symfony.tar.gz

RUN mv symfony /bin/

USER www-owner

ARG MAIL
ARG SIGNATURE

RUN git config --global user.email $MAIL

RUN git config --global user.name $SIGNATURE

USER root

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

ADD customisation/php.ini /etc/php/php.ini

WORKDIR /srv/http

CMD apachectl -D FOREGROUND
