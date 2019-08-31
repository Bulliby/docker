FROM archlinux/base

RUN useradd "aur" -ms /bin/bash

COPY mirrorlist /etc/pacman.d/mirrorlist

RUN pacman -Syyu --noconfirm wget

WORKDIR /home/aur

RUN wget "https://aur.archlinux.org/cgit/aur.git/snapshot/php56.tar.gz"

RUN pacman -S --noconfirm tar

RUN tar -xf php56.tar.gz

WORKDIR  /home/aur/php56

RUN chown -R aur:aur . 

RUN pacman -S --noconfirm base-devel

RUN pacman -S --noconfirm apache c-client postgresql-libs smtp-forwarder unixodbc net-snmp libzip enchant freetds libmcrypt tidyhtml aspell gd libxslt openssl-1.0 libnsl

USER aur

RUN gpg --recv-keys C2BF0BC433CFC8B3

RUN makepkg

USER root

RUN pacman -U --noconfirm php56-5.6.40-1-x86_64.pkg.tar.xz php56-apache-5.6.40-1-x86_64.pkg.tar.xz

RUN pacman -S --noconfirm vim

COPY httpd.conf /etc/httpd/conf/httpd.conf

EXPOSE 80

RUN echo "<?php echo 'Hello World' . PHP_EOL;" > /srv/http/index.php

CMD apachectl -D FOREGROUND
