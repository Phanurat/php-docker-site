FROM php:7.4-fpm

WORKDIR /var/www/html

# Update and install system dependencies and PHP extensions
RUN apt-get update -y && \
    apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libxml2-dev \
    openssl \
    libfreetype6-dev \
    libjpeg62-turbo-dev && \
    pecl install imagick && \
    docker-php-ext-enable imagick && \
    docker-php-ext-install pdo pdo_mysql mysqli mbstring exif pcntl bcmath && \
    docker-php-ext-configure gd --with-freetype --with-jpeg=/usr/include/ && \
    docker-php-ext-install -j$(nproc) gd && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

COPY php.ini "$PHP_INI_DIR/conf.d/"
