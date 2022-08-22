FROM waxer/php:8.1

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf
ADD customisation/php.ini /etc/php/php.ini

WORKDIR /srv/http

RUN sed -i 's/variables_order = \"GPCS\"//' /etc/php/php.ini

CMD apachectl -D FOREGROUND
