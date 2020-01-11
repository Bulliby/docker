FROM archlinux/base

RUN useradd "aur" -ms /bin/bash

COPY mirrorlist /etc/pacman.d/mirrorlist

RUN pacman -Syyu --noconfirm wget

WORKDIR /home/aur

RUN wget "https://aur.archlinux.org/cgit/aur.git/snapshot/php72.tar.gz"

RUN pacman -S --noconfirm tar

RUN tar -xf php72.tar.gz

WORKDIR  /home/aur/php72

RUN chown -R aur:aur . 

RUN pacman -S --noconfirm base-devel

RUN pacman -S --noconfirm apache aspell c-client enchant gd libmcrypt libxslt libzip net-snmp postgresql-libs tidy unixodbc freetds libsodium

USER aur

RUN makepkg

RUN pacman -U --noconfirm php56-5.6.40-1-x86_64.pkg.tar.xz php56-apache-5.6.40-1-x86_64.pkg.tar.xz

RUN pacman -S --noconfirm vim

COPY httpd.conf /etc/httpd/conf/httpd.conf

EXPOSE 80

RUN echo "<?php echo 'Hello World' . PHP_EOL;" > /srv/http/index.php

CMD apachectl -D FOREGROUND
