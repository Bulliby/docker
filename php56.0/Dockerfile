FROM archlinux/base

COPY mirrorlist /etc/pacman.d/mirrorlist

RUN pacman -Syyu --noconfirm wget

RUN mkdir build

WORKDIR /home/build

RUN wget "https://www.php.net/distributions/php-5.6.0.tar.gz"

RUN pacman -Syyu --noconfirm tar

RUN tar -xf "php-5.6.0.tar.gz"

WORKDIR /home/build/php-5.6.0

RUN pacman -S --noconfirm base-devel

RUN ./configure

RUN make

EXPOSE 80

CMD apachectl -D FOREGROUND

