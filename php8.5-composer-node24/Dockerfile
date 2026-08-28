FROM php:8.5
LABEL authors="move elevator GmbH"
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

# Node is pulled from a trixie variant to match the base image's Debian release, so the copied
# binary finds the glibc it was built against. The tag floats within the major: frontend builds
# and release tooling only ever constrain the major via the projects' package.json "engines".
COPY --from=node:24-trixie-slim /usr/local/bin/node /usr/local/bin/node
COPY --from=node:24-trixie-slim /usr/local/lib/node_modules /usr/local/lib/node_modules
RUN ln -s ../lib/node_modules/npm/bin/npm-cli.js /usr/local/bin/npm \
    && ln -s ../lib/node_modules/npm/bin/npx-cli.js /usr/local/bin/npx

RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends \
    git \
    libavif-dev \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libsodium-dev \
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
    && docker-php-ext-install gd intl sodium

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
    libsodium-dev \
    libwebp-dev \
    && rm -rf /var/lib/apt/lists/* /usr/src/*
