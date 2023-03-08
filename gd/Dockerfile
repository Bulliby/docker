FROM waxer/php8.1

RUN pacman -Syyu --noconfirm php-gd

RUN sed -i 's|;extension=gd|extension=gd|' /etc/php/php.ini

CMD apachectl -D FOREGROUND
