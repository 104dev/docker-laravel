FROM php:8.0-fpm

COPY php.ini /usr/local/etc/php/

#pdo_mysqlのインストール
#libpq-dev+pdo_pgsql
#herokuのインストール

RUN apt-get update && apt-get install -y \
  unzip \
  libzip-dev \
  zlib1g-dev \
  libpq-dev \
  git \
  make \
  curl \
  xz-utils \
  file \
  && docker-php-ext-install \
  zip \
  pdo_mysql \
  pdo_pgsql \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* 

#Composerのインストール
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

#node.jsのインストール
RUN curl -SL https://deb.nodesource.com/setup_lts.x | bash
RUN apt-get install -y nodejs && \
  npm install -g npm@latest

RUN echo 'max_execution_time = 600' >> /usr/local/etc/php/conf.d/docker-php-maxexectime.ini;
  
WORKDIR /var/www/html