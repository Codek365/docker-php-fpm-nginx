FROM php:8.1-fpm

# Set working directory
WORKDIR /var/www

# Install dependencies
RUN apt update && apt -y install wget zip unzip git vim npm

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
RUN chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions gd gmp exif @composer zip
RUN docker-php-ext-install mysqli pdo pdo_mysql && docker-php-ext-enable pdo_mysql

# RUN apt update && apt -y install vim

# Expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["php-fpm"]