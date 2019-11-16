FROM waxer/php73:v1

WORKDIR /home/aur

RUN pacman -Syyu --noconfirm wget

RUN wget "https://aur.archlinux.org/cgit/aur.git/snapshot/v8.tar.gz"

RUN tar -xf v8.tar.gz

WORKDIR  /home/aur/v8

RUN chown -R aur:aur . 

RUN pacman -Syyu --noconfirm  clang clang-tools-extra  python2  python2-colorama python2-pylint python2-lazy-object-proxy python2-singledispatch python2-wrapt ninja

USER aur

ARG VERSION

RUN sed s/pkgver\=\[0-9.\]\*/pkgver\="$VERSION"/ PKGBUILD > PKGBUILD_new

RUN mv PKGBUILD_new PKGBUILD

RUN makepkg

USER root

RUN pacman -U --noconfirm v8*.pkg.tar.xz

WORKDIR  /usr/local/src

RUN git clone https://github.com/phpv8/v8js.git

WORKDIR  /usr/local/src/v8js

RUN phpize

RUN ./configure

RUN make

RUN make install

RUN echo extension=v8js.so >> /etc/php/php.ini

CMD apachectl -D FOREGROUND
