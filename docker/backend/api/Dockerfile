FROM dunglas/frankenphp

ENV TZ Asia/Tokyo

COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/
COPY --from=composer:2.7 /usr/bin/composer /usr/bin/composer

RUN apt-get update && apt-get upgrade -y && \
  apt -y install git \
  zip unzip
RUN install-php-extensions \
  opcache \
  pcntl

COPY ./backend/api/src /app

WORKDIR /app

COPY ./docker/backend/api/php.ini /usr/local/etc/php/php.ini

ENTRYPOINT ["php", "artisan", "octane:frankenphp"]