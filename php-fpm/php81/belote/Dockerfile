FROM waxer/php81-fpm

WORKDIR /home/aur/php81

RUN  pacman --noconfirm -U  \
                php81-phar-*x86_64.pkg.tar.zst \
                php81-ctype-*x86_64.pkg.tar.zst \
                php81-cli-*x86_64.pkg.tar.zst \
                php81-curl-*x86_64.pkg.tar.zst \
                php81-dom-*x86_64.pkg.tar.zst \
                php81-fileinfo-*x86_64.pkg.tar.zst \
                php81-mbstring-*x86_64.pkg.tar.zst \
                php81-openssl-*x86_64.pkg.tar.zst \
                php81-pdo-*x86_64.pkg.tar.zst \
                php81-tokenizer-*x86_64.pkg.tar.zst \
                php81-xml-*x86_64.pkg.tar.zst \
                php81-xmlwriter-*x86_64.pkg.tar.zst \
                php81-mysql-*x86_64.pkg.tar.zst \
                php81-simplexml-*x86_64.pkg.tar.zst

COPY belote.conf /etc/php81/php-fpm.d/belote.conf

RUN mv /usr/bin/php81 /usr/bin/php

WORKDIR /srv/http

CMD ["php-fpm81", "-F"]
