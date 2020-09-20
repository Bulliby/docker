FROM waxer/php74:v1

RUN sed 's/variables_order = \"GPCS\"//' /etc/php/php.ini > /etc/php/php.ini.new

RUN mv /etc/php/php.ini.new /etc/php/php.ini
