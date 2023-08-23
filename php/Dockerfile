FROM php:8.1.13-fpm-alpine3.16

RUN apk update && \
    apk add --no-cache \
        curl \
        git \
        graphicsmagick \
        gnupg \
        imagemagick \
        jq \
        icu-dev \
        libpng-dev \
        libxslt-dev \
        libzip-dev \
        mariadb-client \
        moreutils \
        nano \
        net-tools \
        nodejs \
        npm \
        procps \
        unzip \
        vim \
        wget \
        zip

RUN docker-php-ext-install \
        bcmath \
        gd \
        intl \
        opcache \
        pdo_mysql \
        soap \
        xml \
        xsl \
        zip && \
    ln -s /usr/lib/x86_64-linux-gnu/ImageMagick-6.8.9/bin-Q16/MagickWand-config /usr/bin/ && \
    rm -rf /var/lib/apt/lists/*

#RUN printf "\n" | pecl install imagick
#RUN docker-php-ext-enable imagick

RUN docker-php-ext-install exif

# Install Composer globally
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
ENV PATH "${PATH}:/root/.composer/vendor/bin"

# Install Grunt CLI
RUN npm install -g grunt-cli

# Install Yarn
RUN npm install -g yarn

RUN apk add --no-cache $PHPIZE_DEPS \
    && pecl install xdebug-3.1.3 \
    && docker-php-ext-enable xdebug \
    && echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.client_host=host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

#RUN usermod -u 1000 www-data
