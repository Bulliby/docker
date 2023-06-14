FROM waxer/php81-fpm

WORKDIR /home/aur/php81

RUN  pacman --noconfirm -U  php81-ctype-*x86_64.pkg.tar.zst \
                php81-curl-*x86_64.pkg.tar.zst \
                php81-dom-*x86_64.pkg.tar.zst \
                php81-fileinfo-*x86_64.pkg.tar.zst \
                php81-mbstring-*x86_64.pkg.tar.zst \
                php81-openssl-*x86_64.pkg.tar.zst \
                php81-pdo-*x86_64.pkg.tar.zst \
                php81-tokenizer-*x86_64.pkg.tar.zst \
                php81-xml-*x86_64.pkg.tar.zst 

COPY belote.conf /etc/php81/php-fpm.d/belote.conf

WORKDIR /srv/http

CMD ["php-fpm81", "-F"]
