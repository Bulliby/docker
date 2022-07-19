FROM archlinux:base

# First to be --uid 1000 / This is the standard user to interact with files
# in host and guest
RUN useradd "www-owner" -ms /bin/bash

RUN useradd "aur" -ms /bin/bash

COPY mirrorlist /etc/pacman.d/mirrorlist

WORKDIR /home/aur

RUN pacman -Syyu --noconfirm apache base-devel oniguruma icu

ADD build /home/aur/

RUN chown -R aur:aur . 

USER aur

RUN makepkg -d --skipinteg --nocheck

USER root

RUN pacman -U --noconfirm php-8.1.*.pkg.tar.zst

RUN pacman -S --noconfirm vim composer git

RUN curl -o symfony.tar.gz -L --max-redirs 1 https://github.com/symfony-cli/symfony-cli/releases/download/v5.4.11/symfony-cli_linux_amd64.tar.gz

RUN tar -xf symfony.tar.gz

RUN mv symfony /bin/

WORKDIR  /etc/httpd/conf

RUN sed -i 's|#Include conf/extra/httpd-vhosts.conf|Include conf/extra/httpd-vhosts.conf|' /etc/httpd/conf/httpd.conf

RUN sed -i 's|#LoadModule mpm_prefork_module modules/mod_mpm_prefork.so|LoadModule mpm_prefork_module modules/mod_mpm_prefork.so|' /etc/httpd/conf/httpd.conf

RUN sed -i 's|LoadModule mpm_event_module modules/mod_mpm_event.so|#LoadModule mpm_event_module modules/mod_mpm_event.so|' /etc/httpd/conf/httpd.conf

RUN echo 'LoadModule php_module modules/libphp.so' >> /etc/httpd/conf/httpd.conf

RUN echo 'AddHandler php-script php' >> /etc/httpd/conf/httpd.conf

RUN echo 'Include conf/extra/php_module.conf' >> /etc/httpd/conf/httpd.conf

RUN rm -rf /home/aur

ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

WORKDIR /srv/http

RUN pacman -S --noconfirm xdebug

ADD conf/xdebug.ini /etc/php/conf.d/xdebug.ini

CMD apachectl -D FOREGROUND
