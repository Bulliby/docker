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

EXPOSE 80

CMD apachectl -D FOREGROUND
