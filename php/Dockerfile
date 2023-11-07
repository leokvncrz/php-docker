FROM php:7.4.19-fpm
RUN apt-get update && \
    apt-get install -y libxml2-dev && \
    apt-get -y install wget
RUN docker-php-ext-install soap && docker-php-ext-enable soap
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN pecl install xdebug-3.1.0 && docker-php-ext-enable xdebug pdo_mysql
RUN apt-get update && apt-get install -y libmagickwand-dev --no-install-recommends && rm -rf /var/lib/apt/lists/*
RUN printf "\n" | pecl install imagick
RUN docker-php-ext-enable imagick
RUN docker-php-ext-install gd
RUN chmod go+x /usr/local/bin

RUN apt-get update && apt-get install -y \
    zip \
    libxml2-dev \
    libzip-dev
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
  && docker-php-ext-configure gd --with-freetype --with-jpeg \
  && docker-php-ext-install -j$(nproc) gd
RUN docker-php-ext-install zip 

COPY php/php.ini /usr/local/etc/php/
