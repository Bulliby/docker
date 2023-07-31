FROM waxer/php

RUN pacman -Syyu --noconfirm php-gd

RUN sed -i 's|;extension=gd|extension=gd|' /etc/php/php.ini

RUN sed -i 's|session.auto_start = 0|session.auto_start = 1|' /etc/php/php.ini

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

CMD apachectl -D FOREGROUND
