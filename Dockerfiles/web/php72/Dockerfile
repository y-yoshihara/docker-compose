FROM php:7.2-apache

# 諸々インストール
COPY php.ini /usr/local/etc/php/
RUN echo "date.timezone = Asia/Tokyo" >> /usr/local/etc/php/php.ini

RUN apt-get update && apt-get install -y unzip libmemcached-dev zlib1g-dev
RUN pecl install memcached-3.0.4 && docker-php-ext-enable memcached
RUN pecl install xdebug-2.6.1 && docker-php-ext-enable xdebug
COPY docker-php-ext-xdebug-config.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug-config.ini
RUN docker-php-ext-install mysqli pdo_mysql
RUN curl -sS https://getcomposer.org/installer | php; mv composer.phar /usr/local/bin/composer ; mkdir /var/dev

# apache
ENV APACHE_DOCUMENT_ROOT /var/www/html/public

# apacheのrewriteを有効にする
RUN a2enmod rewrite
#RUN cd /etc/apache2/mods-enabled && ln -s /etc/apache2/mods-available/rewrite.load ./

WORKDIR /var/www/html
