FROM php:7.3-fpm

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        curl \
        dnsutils \
        git \
        git-core \
        graphicsmagick \
        gnupg \
        imagemagick \
        jq \
        libzip-dev \
        libicu-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmagickwand-dev \
        libonig-dev \
        libpng-dev \
        libxslt-dev \
        libssh2-1-dev \
        mailutils \
        mariadb-client \
        moreutils \
        nano \
        netcat \
        net-tools \
        p7zip-full \
        procps \
        ssh \
        telnet \
        unzip \
        vim \
        wget \
        zip && \
    docker-php-ext-install \
        bcmath \
        gd \
        iconv \
        intl \
        opcache \
        pdo_mysql \
        soap \
        xml \
        xsl \
        zip && \
    ln -s /usr/lib/x86_64-linux-gnu/ImageMagick-6.8.9/bin-Q16/MagickWand-config /usr/bin/ && \
    rm -rf /var/lib/apt/lists/*

RUN printf "\n" | pecl install imagick
RUN docker-php-ext-enable imagick

# Install Composer globally
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    composer global require "hirak/prestissimo:dev-master" --no-suggest --optimize-autoloader --classmap-authoritative
ENV PATH "${PATH}:/root/.composer/vendor/bin"

# Install Node.js
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - && \
    apt-get install -y nodejs

# Install Grunt CLI
RUN npm install -g grunt-cli

# Install Yarn
RUN npm install -g yarn

RUN usermod -u 1000 www-data
