FROM waxer/apache

RUN pacman -Syyu --noconfirm php-apache

# PHP stuff
RUN sed -i 's|#LoadModule mpm_prefork_module modules/mod_mpm_prefork.so|LoadModule mpm_prefork_module modules/mod_mpm_prefork.so|' /etc/httpd/conf/httpd.conf

RUN sed -i 's|LoadModule mpm_event_module modules/mod_mpm_event.so|#LoadModule mpm_event_module modules/mod_mpm_event.so|' /etc/httpd/conf/httpd.conf

RUN echo 'LoadModule php_module modules/libphp.so' >> /etc/httpd/conf/httpd.conf

RUN echo 'AddHandler php-script .php' >> /etc/httpd/conf/httpd.conf

RUN echo 'Include conf/extra/php_module.conf' >> /etc/httpd/conf/httpd.conf

RUN sed -i "s|expose_php = On|expose_php = Off|" /etc/php/php.ini

WORKDIR /srv/http

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

CMD apachectl -D FOREGROUND
