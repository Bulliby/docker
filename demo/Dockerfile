FROM waxer/symfony:8.1

RUN pacman -Syyu --noconfirm xdebug php-redis php-igbinary

ADD conf/xdebug.ini /etc/php/conf.d/xdebug.ini

RUN sed -i 's|;extension=redis|extension=redis|' /etc/php/conf.d/redis.ini

RUN sed -i 's|;extension=igbinary.so|extension=igbinary.so|' /etc/php/conf.d/igbinary.ini

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

ADD customisation/php.ini /etc/php/php.ini

WORKDIR /srv/http

CMD apachectl -D FOREGROUND
