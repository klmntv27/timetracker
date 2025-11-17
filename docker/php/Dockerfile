FROM php:8.3-fpm

# Установка системных зависимостей
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libpq-dev \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    curl \
    nodejs \
    npm \
    openssh-server

# Установка расширений PHP
RUN docker-php-ext-install pdo pdo_pgsql mbstring exif pcntl bcmath gd

# Установка Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Создание пользователя
RUN useradd -ms /bin/bash klmntv

# Копирование исходников
WORKDIR /var/www
COPY src/ /var/www/

# Назначение прав
RUN chown -R klmntv:klmntv /var/www

USER klmntv