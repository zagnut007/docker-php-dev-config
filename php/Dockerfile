FROM php:5.6.40-fpm-alpine3.8
RUN apk update; \
    apk upgrade;
#RUN docker-php-ext-install mysql
#RUN docker-php-ext-install mysqli

RUN apk upgrade --update && apk add \
  coreutils \
  freetype-dev \
  libjpeg-turbo-dev \
  libltdl \
  libmcrypt-dev \
  libpng-dev \
&& docker-php-ext-install -j$(nproc) iconv mcrypt \
&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
&& docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install mysql
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install mbstring
#RUN docker-php-ext-install zip
RUN docker-php-ext-install gd