FROM php:7.2-fpm

COPY php.ini /usr/local/etc/php/

# module install
RUN apt-get update -y
RUN apt-get install -y \
  zlib1g-dev \
  mariadb-client \
  unzip
RUN docker-php-ext-install \
  zip \
  pdo_mysql

# Composer install
COPY --from=composer /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin


WORKDIR /var/www
