FROM archlinux/base

COPY mirrorlist /etc/pacman.d/mirrorlist

RUN pacman -Syyu --noconfirm git php php-apache vim

WORKDIR  /etc/httpd/conf

RUN sed s/#Include\ conf\\/extra\\/httpd-vhosts.conf/Include\ conf\\/extra\\/httpd-vhosts.conf/ httpd.conf > /etc/httpd/conf/httpd.conf_new

RUN sed s/#LoadModule\ mpm_prefork_module\ modules\\/mod_mpm_prefork.so\/LoadModule\ mpm_prefork_module\ modules\\/mod_mpm_prefork.so/ /etc/httpd/conf/httpd.conf_new > /etc/httpd/conf/httpd.conf

RUN sed s/LoadModule\ mpm_event_module\ modules\\/mod_mpm_event.so/#LoadModule\ mpm_event_module\ modules\\/mod_mpm_event.so/ /etc/httpd/conf/httpd.conf > /etc/httpd/conf/httpd.conf_new

RUN mv httpd.conf_new httpd.conf

RUN echo 'LoadModule php7_module modules/libphp7.so' >> /etc/httpd/conf/httpd.conf

RUN echo 'AddHandler php7-script php' >> /etc/httpd/conf/httpd.conf

RUN echo 'Include conf/extra/php7_module.conf' >> /etc/httpd/conf/httpd.conf

RUN echo 'LoadModule rewrite_module modules/mod_rewrite.so' >> /etc/httpd/conf/httpd.conf

RUN echo 'extension=pdo_mysql' >> /etc/php/php.ini
RUN echo 'extension=mysqli' >> /etc/php/php.ini

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

EXPOSE 80

CMD apachectl -D FOREGROUND
