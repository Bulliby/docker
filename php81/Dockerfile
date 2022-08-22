FROM archlinux:base

# First to be --uid 1000 / This is the standard user to interact with files
# in host and guest
RUN useradd "www-owner" -ms /bin/bash

RUN useradd "aur" -ms /bin/bash

COPY mirrorlist /etc/pacman.d/mirrorlist

RUN pacman -Syyu --noconfirm vim apache php-apache

WORKDIR  /etc/httpd/conf

RUN sed -i 's|#Include conf/extra/httpd-vhosts.conf|Include conf/extra/httpd-vhosts.conf|' /etc/httpd/conf/httpd.conf

RUN sed -i 's|#LoadModule mpm_prefork_module modules/mod_mpm_prefork.so|LoadModule mpm_prefork_module modules/mod_mpm_prefork.so|' /etc/httpd/conf/httpd.conf

RUN sed -i 's|LoadModule mpm_event_module modules/mod_mpm_event.so|#LoadModule mpm_event_module modules/mod_mpm_event.so|' /etc/httpd/conf/httpd.conf

RUN echo 'LoadModule php_module modules/libphp.so' >> /etc/httpd/conf/httpd.conf

RUN echo 'AddHandler php-script php' >> /etc/httpd/conf/httpd.conf

RUN echo 'Include conf/extra/php_module.conf' >> /etc/httpd/conf/httpd.conf

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

WORKDIR /srv/http

CMD apachectl -D FOREGROUND
