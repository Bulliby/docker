FROM waxer/php

RUN pacman -Syyu --noconfirm php-gd diffutils

RUN sed -i 's|;extension=gd|extension=gd|' /etc/php/php.ini

CMD apachectl -D FOREGROUND
