FROM php:7.4-fpm

# Set working directory
WORKDIR /var/www/myapp

RUN apt-get update && apt-get install -y \
    build-essential \
    libicu-dev \
    libpng-dev \
    libzip-dev\
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    nano \
    unzip \
    git \
    curl \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    sudo \
    openssl \
    libssl-dev \
    xdebug

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/* 

# Install extensions
RUN docker-php-ext-install mysqli pdo_mysql zip exif pcntl

RUN docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg
RUN docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-configure intl 
RUN docker-php-ext-install intl

# Add user for laravel application
RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

# Copy existing application directory contents
COPY . /var/www/myapp/

# Copy existing application directory permissions
COPY --chown=www:www . /var/www/myapp/

# Change current user to www
USER www

# Expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["php-fpm"]

