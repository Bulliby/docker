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

USER root

EXPOSE 80

CMD apachectl -D FOREGROUND
