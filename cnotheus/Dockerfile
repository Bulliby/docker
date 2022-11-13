FROM waxer/apache

WORKDIR /srv/http

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

CMD apachectl -D FOREGROUND
