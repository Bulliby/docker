FROM waxer/symfony:8.1

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

WORKDIR /srv/http

CMD apachectl -D FOREGROUND
