FROM php:5

RUN apt-get update && apt-get install -y unzip libmemcached-dev zlib1g-dev
RUN docker-php-ext-install mysqli pdo_mysql
RUN pecl install memcached-2.2.0 && docker-php-ext-enable memcached
RUN curl -sS https://getcomposer.org/installer | php; mv composer.phar /usr/local/bin/composer ; mkdir /var/dev
RUN pecl install xdebug-2.5.5 && docker-php-ext-enable xdebug

RUN mkdir /var/www && mkdir /var/www/html
COPY php.ini /usr/local/etc/php/
RUN echo "date.timezone = Asia/Tokyo" >> /usr/local/etc/php/php.ini

WORKDIR /var/www/html

CMD ["bash"]
