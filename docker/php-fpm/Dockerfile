FROM php:8.1-fpm
RUN docker-php-ext-install pdo pdo_mysql
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ADD config/docker-xdebug.ini /usr/local/etc/php/conf.d/docker-xdebug.ini

RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

COPY . /var/www

COPY --chown=www:www . /var/www

USER www

WORKDIR /var/www
