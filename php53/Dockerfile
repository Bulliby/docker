FROM archlinux/base

RUN useradd "aur" -ms /bin/bash

COPY mirrorlist /etc/pacman.d/mirrorlist

RUN pacman -Syyu --noconfirm wget

WORKDIR /home/aur

RUN wget "https://aur.archlinux.org/cgit/aur.git/snapshot/php53.tar.gz"

RUN pacman -S --noconfirm tar

RUN tar -xf php53.tar.gz

WORKDIR  /home/aur/php53

RUN chown -R aur:aur . 

RUN pacman -S --noconfirm base-devel

RUN pacman -S --noconfirm apache c-client postgresql-libs libldap smtp-forwarder sqlite unixodbc net-snmp libzip enchant file freetds libmcrypt tidyhtml aspell libltdl libpng libjpeg freetype2 icu curl libxslt openssl-1.0 db gmp systemd patchelf

USER aur

COPY PKGBUILD .

RUN makepkg

USER root

RUN pacman -U --noconfirm php53-5.3.29-x86_64.pkg.tar.xz php53-apache-5.3.29-x86_64.pkg.tar.xz

RUN pacman -S --noconfirm vim

COPY httpd.conf /etc/httpd/conf/httpd.conf

EXPOSE 80

RUN echo "<?php echo 'Hello World' . PHP_EOL;" > /srv/http/index.php

CMD apachectl -D FOREGROUND
