FROM ubuntu:18.04
RUN ln -snf /usr/share/zoneinfo/Europe/Paris /etc/localtime
RUN apt-get update && apt-get install -my \
  curl \
  wget \
  php-curl \
  php-fpm \
  php-gd \
  php-xsl \
  php-mysqlnd \
  php-cli \
  php-intl \
  php-bz2 \
  php-zip \
  php-mbstring \
  git \
  zip \
  php-apcu \
  php-redis \
  php-opcache
RUN mkdir /run/php
ADD conf/www.conf /etc/php/7.2/fpm/pool.d/www.conf
ADD conf/php-fpm.conf /etc/php/7.2/fpm/php-fpm.conf
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer
WORKDIR /var/www/html/symfony
EXPOSE 9000
CMD ["php-fpm7.2"]
