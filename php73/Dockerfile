FROM archlinux/base

RUN useradd "aur" -ms /bin/bash

COPY mirrorlist /etc/pacman.d/mirrorlist

RUN pacman -Syyu --noconfirm wget

WORKDIR /home/aur

RUN wget "https://aur.archlinux.org/cgit/aur.git/snapshot/php73.tar.gz"

RUN pacman -S --noconfirm tar

RUN tar -xf php73.tar.gz

WORKDIR  /home/aur/php73

RUN chown -R aur:aur . 

RUN pacman -Syyu --noconfirm base-devel

RUN pacman -Syyu --noconfirm apache aspell c-client enchant gd libsodium libxslt libzip net-snmp postgresql-libs tidy unixodbc postfix freetds libnsl procps-ng

USER aur

RUN gpg --recv-keys D66C9593118BCCB6

RUN makepkg --nocheck

USER root

RUN pacman -U --noconfirm php73-7.3*.pkg.tar.xz php73-apache*.pkg.tar.xz

RUN pacman -Syyu --noconfirm vim

WORKDIR  /etc/httpd/conf

RUN sed s/#Include\ conf\\/extra\\/httpd-vhosts.conf/Include\ conf\\/extra\\/httpd-vhosts.conf/ httpd.conf > /etc/httpd/conf/httpd.conf_new

RUN sed s/#LoadModule\ mpm_prefork_module\ modules\\/mod_mpm_prefork.so\/LoadModule\ mpm_prefork_module\ modules\\/mod_mpm_prefork.so/ /etc/httpd/conf/httpd.conf_new > /etc/httpd/conf/httpd.conf

RUN sed s/LoadModule\ mpm_event_module\ modules\\/mod_mpm_event.so/#LoadModule\ mpm_event_module\ modules\\/mod_mpm_event.so/ /etc/httpd/conf/httpd.conf > /etc/httpd/conf/httpd.conf_new

RUN mv httpd.conf_new httpd.conf

RUN echo 'LoadModule php7_module modules/libphp7.so' >> /etc/httpd/conf/httpd.conf

RUN echo 'AddHandler php7-script php' >> /etc/httpd/conf/httpd.conf

RUN echo 'Include conf/extra/php7_module.conf' >> /etc/httpd/conf/httpd.conf

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

EXPOSE 80

CMD apachectl -D FOREGROUND
