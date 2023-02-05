FROM waxer/php81-fpm

WORKDIR /home/aur/php81

RUN pacman -S --noconfirm libxml2

RUN  pacman --noconfirm -U  php81-ctype-*x86_64.pkg.tar.zst \
                php81-curl-*x86_64.pkg.tar.zst \
                php81-dom-*x86_64.pkg.tar.zst \
                php81-gd-*x86_64.pkg.tar.zst \
                php81-mbstring-*x86_64.pkg.tar.zst \
                php81-posix-*x86_64.pkg.tar.zst \
                php81-simplexml-*x86_64.pkg.tar.zst \
                php81-xml-*x86_64.pkg.tar.zst \
                php81-xmlreader-*x86_64.pkg.tar.zst \
                php81-xmlwriter-*x86_64.pkg.tar.zst \
                php81-zip-*x86_64.pkg.tar.zst \
                php81-pdo-*x86_64.pkg.tar.zst \
                php81-intl-*x86_64.pkg.tar.zst \
                php81-bz2-*x86_64.pkg.tar.zst \
                php81-cli-*x86_64.pkg.tar.zst \
                php81-mysql-*x86_64.pkg.tar.zst \
                php81-openssl-*x86_64.pkg.tar.zst 

COPY nextcloud.conf /etc/php81/php-fpm.d/www.conf

CMD ["php-fpm81", "-F"]
