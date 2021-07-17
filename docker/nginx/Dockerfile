FROM nginx:alpine

# Make Directory - Workspace
RUN mkdir -p /var/www/myapp

RUN apk update && apk add \
    nano \
    openssl 

# ADD and set Group
RUN addgroup -g 1000 laravel && adduser -G laravel -g laravel -s /bin/sh -D laravel

# Set Group to Workspace
RUN chown laravel:laravel /var/www/myapp