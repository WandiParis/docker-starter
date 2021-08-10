FROM php:7.4-fpm-alpine3.13

RUN apk add --update \
        icu-dev \
        libzip-dev zip unzip \
        chromium \
        chromium-chromedriver \
        nodejs \
        rabbitmq-c rabbitmq-c-dev \
        freetype-dev \
        libjpeg-turbo-dev \
        libpng-dev \
    && apk add --no-cache $PHPIZE_DEPS \
    && pecl install \
        xdebug \
        apcu \
        amqp \
    && docker-php-ext-install \
        opcache \
        intl \
		pdo_mysql \
        zip \
        gd \
    && docker-php-ext-enable \
        xdebug \
        apcu \
        opcache \
        amqp \
        gd

RUN rm -rf /var/cache/apk/* \
    && rm -rf /tmp/*

# composer
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --version=1.10.17

RUN chown 1000:1000 -R . && chmod 777 -R .

# panther
ENV PANTHER_NO_SANDBOX 1
ENV PANTHER_CHROME_DRIVER_BINARY /usr/lib/chromium/chromedriver
ENV PANTHER_WEB_SERVER_PORT 9080
