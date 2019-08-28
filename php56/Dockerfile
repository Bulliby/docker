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

EXPOSE 80

CMD apachectl -D FOREGROUND
