FROM waxer/symfony AS prod

RUN pacman -Syyu --noconfirm php-redis php-igbinary

RUN sed -i 's|;extension=redis|extension=redis|' /etc/php/conf.d/redis.ini

RUN sed -i 's|;extension=igbinary.so|extension=igbinary.so|' /etc/php/conf.d/igbinary.ini

WORKDIR /srv/http

CMD apachectl -D FOREGROUND

FROM prod AS dev

RUN pacman -Syyu --noconfirm xdebug

ADD conf/xdebug.ini /etc/php/conf.d/xdebug.ini
