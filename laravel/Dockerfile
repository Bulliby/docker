FROM waxer/php8.1 AS prod

WORKDIR /srv/http

CMD apachectl -D FOREGROUND

FROM prod AS dev

RUN pacman -Syyu --noconfirm xdebug

ADD conf/xdebug.ini /etc/php/conf.d/xdebug.ini
