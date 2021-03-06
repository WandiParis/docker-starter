FROM php:7.1-fpm-alpine

RUN apk add --update \
        icu-dev \
        zlib-dev \
        chromium \
        chromium-chromedriver \
        nodejs \
        rabbitmq-c rabbitmq-c-dev \
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
    && docker-php-ext-enable \
        xdebug \
        apcu \
        opcache \
        amqp

RUN rm -rf /var/cache/apk/* \
    && rm -rf /tmp/*

# composer
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN curl --insecure https://getcomposer.org/composer.phar -o /usr/bin/composer \
    && chmod +x /usr/bin/composer

RUN chown 1000:1000 -R . && chmod 777 -R .

# panther
ENV PANTHER_NO_SANDBOX 1
ENV PANTHER_CHROME_DRIVER_BINARY /usr/lib/chromium/chromedriver
ENV PANTHER_WEB_SERVER_PORT 9080