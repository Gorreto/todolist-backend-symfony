FROM php:7.2-fpm
LABEL maintainer="fernandez.fabien38@gmail.fr"

# Installing dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    mysql-client \
    libpng-dev \
    locales \
    zip

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Installing extensions
RUN docker-php-ext-install pdo_mysql gd mbstring zip

# Installing composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Setting locales
RUN echo fr_FR.UTF-8 UTF-8 > /etc/locale.gen && locale-gen

# Allow container to write on host
RUN usermod -u 1000 www-data

# Changing Workdir
WORKDIR /application