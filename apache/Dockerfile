FROM archlinux:base

# First to have a --uid 1000 
RUN useradd "www-owner" -ms /bin/bash

RUN useradd "aur" -ms /bin/bash

RUN pacman -Syyu --noconfirm vim apache 

# Add Vhost conf
RUN sed -i 's|#Include conf/extra/httpd-vhosts.conf|Include conf/extra/httpd-vhosts.conf|' /etc/httpd/conf/httpd.conf

RUN echo -e "ServerTokens Prod\nServerSignature Off" >> /etc/httpd/conf/httpd.conf

WORKDIR /srv/http

# Copy Vhost file. At the end because it often change
ADD conf/vhost.conf /etc/httpd/conf/extra/httpd-vhosts.conf

CMD apachectl -D FOREGROUND
