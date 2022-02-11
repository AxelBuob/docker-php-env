FROM php:7.4-apache

ARG user
ARG uid

RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    locales  \
    libicu-dev \
    libpng-dev \
    libxml2-dev \
    libzip-dev \
    libonig-dev \
    libxslt-dev\
    apt-utils\
    npm

RUN npm install --global yarn

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
    echo "fr_FR.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen

RUN useradd -G www-data,root -u $uid -d /home/$user $user
RUN mkdir -p /home/$user/.composer && \
    chown -R $user:$user /home/$user

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN docker-php-ext-configure intl
RUN docker-php-ext-install \
    pdo \
    pdo_mysql \
    gd \
    opcache \
    intl \
    zip \
    calendar \
    dom \
    mbstring \
    zip \
    gd \
    xsl \
    exif \
    pcntl \
    bcmath
RUN pecl install apcu && docker-php-ext-enable apcu

WORKDIR /var/www/