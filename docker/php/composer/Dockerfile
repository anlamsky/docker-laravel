FROM composer:latest

RUN mkdir -p /var/www/myapp

# ADD and set Group
RUN addgroup -g 1000 laravel && adduser -G laravel -g laravel -s /bin/sh -D laravel

# Set Profile to All Files
RUN chown laravel:laravel /var/www/myapp

# Run in work space
WORKDIR /var/www/myapp