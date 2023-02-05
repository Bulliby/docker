FROM archlinux:base

# ID 1000
RUN useradd "www-owner" -s /bin/bash

RUN useradd "aur" -ms /bin/bash

RUN pacman -Syyu --noconfirm vim 

ENV BUILD_NEEDED \
    libedit \
    pcre

ENV BUILD_DEP \
        git \
        base-devel \
        patchelf \
        python \
        apache \
        libxslt \
        lmdb \
        postgresql-libs \
        unixodbc \
        libfbclient \
        freetds \
        gd \
        tidy \
        libzip \
        oniguruma \
        aspell \
        enchant \
        libvoikko \
        hspell \
        hunspell \
        nuspell \
        aspell \
        net-snmp \
        libsodium \
        msmtp-mta

RUN pacman -Syyu --noconfirm $BUILD_DEP $BUILD_NEEDED

WORKDIR /home/aur

USER aur

RUN git clone https://aur.archlinux.org/php81.git

RUN git clone https://aur.archlinux.org/c-client.git

WORKDIR /home/aur/c-client

RUN makepkg

USER root

RUN pacman -U c-client*.pkg.* --noconfirm

USER aur

WORKDIR /home/aur/php81

RUN makepkg

USER root

RUN pacman -U php81-8* php81-fpm* --noconfirm

RUN pacman -Rs --noconfirm $BUILD_DEP c-client

CMD ["php-fpm81", "-F"]
