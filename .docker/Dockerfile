# docker build . -t pizelli/webserver:1.1

FROM ubuntu:latest

ENV timezone=America/Sao_Paulo

RUN apt-get update && \
    ln -snf /usr/share/zoneinfo/${timezone} /etc/localtime && echo ${timezone} > /etc/timezone && \
    apt-get install -y apache2 && \
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:ondrej/php && \
    apt-get update && \
    apt-get install -y php7.4 && \
    apt-get install -y php-xdebug && \
    apt-get install -y php7.4-mysql && \
    apt-get install -y php7.4-sqlite && \
    apt-get install -y php7.4-bcmath && \
    apt-get install -y php7.4-bz2 && \
    apt-get install -y php7.4-intl && \
    apt-get install -y php7.4-gd && \
    apt-get install -y php7.4-mbstring && \
    apt-get install -y php7.4-zip && \
    apt-get install -y php7.4-xml && \
    apt-get install -y php7.4-curl && \
    apt-get install -y git && \
    a2enmod rewrite && \
    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php && \
    rm composer-setup.php && \
    mv composer.phar /usr/local/bin/composer && \
    chmod a+x /usr/local/bin/composer

COPY ./vhost.conf /etc/apache2/sites-available/000-default.conf

EXPOSE 80

WORKDIR /var/www/html

ENTRYPOINT /etc/init.d/apache2 start && /bin/bash

CMD ["true"]
