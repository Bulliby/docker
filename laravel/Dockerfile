FROM waxer/php AS prod

WORKDIR /srv/http

RUN pacman -Syyu --noconfirm composer

ADD conf/php.ini /etc/php/php.ini

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

CMD apachectl -D FOREGROUND

FROM prod AS dev

RUN pacman -Syyu --noconfirm xdebug

ADD conf/xdebug.ini /etc/php/conf.d/xdebug.ini
