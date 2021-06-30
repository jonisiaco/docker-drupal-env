FROM php:8.0.6-fpm

RUN apt-get -qq update && apt-get -qq -y install  \
    automake \
    cmake \
    g++ \
    git \
    libicu-dev \
    libmagickwand-dev \
    libpng-dev \
    libreadline-dev \
    pkg-config \
    ssh-client \
    supervisor \
    libzip-dev \
    zlib1g-dev \
  && docker-php-ext-install \
    bcmath \
    gd \
    intl \
    opcache \
    pdo_mysql \
    sockets \
    zip \
#    
    && pecl install xdebug igbinary \
    && docker-php-ext-enable xdebug igbinary \
    && version=$(php -r "echo PHP_MAJOR_VERSION.PHP_MINOR_VERSION;") \
    && rm -rf /var/lib/apt/lists/*

# Composer install
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set pid file to be able to restart php-fpm
RUN sed -i "s@^\[global\]@\[global\]\n\npid = /run/php-fpm.pid@" ${PHP_INI_DIR}-fpm.conf

# Add some custom config
#COPY ./php.ini ${PHP_INI_DIR}/conf.d/php.ini
COPY ./php.ini /usr/local/etc/php/php.ini

# Needed for docker-machine
RUN usermod -u 1000 www-data

WORKDIR /var/www

CMD php-fpm

EXPOSE 9000
