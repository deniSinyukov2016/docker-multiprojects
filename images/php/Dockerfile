FROM php:7.2-fpm

ENV COMPOSER_ALLOW_SUPERUSER 1

RUN apt-get update && apt-get install -y \
    libxml2-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libjpeg-dev \
    libpq-dev \
    libmemcached-dev \
    libxslt-dev \
    curl \
    zip \
    git

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install mbstring mysqli gd pdo_mysql pdo_pgsql soap xml zip calendar exif gettext pcntl shmop sockets sysvmsg sysvsem sysvshm wddx xsl

RUN apt-get install -y gnupg \
    && curl -sS https://getcomposer.org/installer -o composer-setup.php \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer
RUN curl -sS https://deb.nodesource.com/setup_8.x | bash - \
    && apt-get install -y build-essential nodejs

# Добавим свой php.ini, можем в нем определять свои значения конфига
ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini

# Указываем рабочую директорию для PHP
WORKDIR /var/www

CMD ["php-fpm"]
