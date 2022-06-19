FROM archlinux:base

RUN useradd "aur" -ms /bin/bash

COPY mirrorlist /etc/pacman.d/mirrorlist

WORKDIR /home/aur

ADD build/* /home/aur/

RUN chown -R aur:aur . 

RUN pacman -Syyu --noconfirm apache curl libzip base-devel

USER aur

RUN gpg --recv-keys F1F692238FBC1666E5A5CCD4199F9DFEF6FFBAFD

RUN makepkg 

USER root

RUN pacman -U --noconfirm php-8.1.*.pkg.tar.zst

RUN pacman -S --noconfirm vim composer

WORKDIR  /etc/httpd/conf

RUN sed -i 's|#Include conf/extra/httpd-vhosts.conf|Include conf/extra/httpd-vhosts.conf|' /etc/httpd/conf/httpd.conf

RUN sed -i 's|#LoadModule mpm_prefork_module modules/mod_mpm_prefork.so|LoadModule mpm_prefork_module modules/mod_mpm_prefork.so|' /etc/httpd/conf/httpd.conf

RUN sed -i 's|LoadModule mpm_event_module modules/mod_mpm_event.so|#LoadModule mpm_event_module modules/mod_mpm_event.so|' /etc/httpd/conf/httpd.conf

RUN echo 'LoadModule php_module modules/libphp.so' >> /etc/httpd/conf/httpd.conf

RUN echo 'AddHandler php-script php' >> /etc/httpd/conf/httpd.conf

RUN echo 'Include conf/extra/php_module.conf' >> /etc/httpd/conf/httpd.conf

RUN rm -rf /home/aur

CMD apachectl -D FOREGROUND
