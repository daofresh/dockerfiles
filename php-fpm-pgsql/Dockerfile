FROM php:8.0.11-fpm
LABEL maintainer "Phan Khac Dao <daofresh.dev@gmail.com>"

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install php-zip
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y \
    libzip-dev unzip
RUN docker-php-ext-configure zip \
    && docker-php-ext-install zip

# Install php-gd
RUN apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev
RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

# Install php-pgsql
RUN apt-get install -y libpq-dev
RUN docker-php-ext-install -j$(nproc) pdo_pgsql pgsql

# Install php-sockets
RUN docker-php-ext-install -j$(nproc) sockets

# Install php-pcntl
RUN docker-php-ext-configure pcntl --enable-pcntl
RUN docker-php-ext-install pcntl
