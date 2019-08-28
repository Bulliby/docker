FROM archlinux/base

RUN useradd "aur" -ms /bin/bash

COPY mirrorlist /etc/pacman.d/mirrorlist

RUN pacman -Syyu --noconfirm git

WORKDIR /home/aur

RUN git clone --branch packages/php  --single-branch https://git.archlinux.org/svntogit/packages.git php73

WORKDIR  /home/aur/php73/repos/extra-x86_64

RUN chown -R aur:aur . 

RUN pacman -S --noconfirm base-devel

RUN pacman -S --noconfirm apache aspell c-client enchant gd libsodium libxslt libzip net-snmp postgresql-libs tidy unixodbc postfix freetds libnsl procps-ng

USER aur

RUN gpg --recv-keys D66C9593118BCCB6

RUN makepkg --nocheck

USER root

EXPOSE 80

CMD apachectl -D FOREGROUND

