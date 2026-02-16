FROM php:8.5
LABEL authors="move elevator GmbH"
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends \
    git \
    libavif-dev \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libwebp-dev \
    openssh-client \
    python3-pip \
    rsync \
    sshpass \
    unzip \
    wget \
    zip \
    && docker-php-ext-configure gd --with-avif --with-freetype --with-jpeg --with-webp \
    && docker-php-ext-configure intl \
    && docker-php-ext-install gd intl

# Install python packages for db and file sync
RUN pip3 install --break-system-packages \
    db-sync-tool-kmi \
    file-sync-tool-kmi

# Cleanup unused packages and cache
RUN apt-get clean \
    && apt-get -y purge \
    libavif-dev \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libwebp-dev \
    && rm -rf /var/lib/apt/lists/* /usr/src/*