FROM ubuntu:xenial

MAINTAINER deyikong

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -yq --no-install-recommends \
    curl \
    # ======= git =====
    git \
    # ======= apache =====
    apache2 \
    # Install php 7
    libapache2-mod-php7.0 \
    php7.0-cli \
    php7.0-json \
    php7.0-curl \
    php7.0-fpm \
    php7.0-gd \
    php7.0-ldap \
    php7.0-mbstring \
    php7.0-mysql \
    php7.0-soap \
    php7.0-sqlite3 \
    php7.0-xml \
    php7.0-zip \
    php7.0-mcrypt \
    php7.0-intl \
    php-imagick \
    php-xdebug \
    # Install tools
    nano \
    graphicsmagick \
    imagemagick \
    ghostscript \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# ======= composer =======
# RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# ======= nodejs =======
# RUN curl -sL https://deb.nodesource.com/setup_6.x | bash - && apt-get install -y nodejs

# Set locales
# RUN locale-gen en_US.UTF-8 en_GB.UTF-8 de_DE.UTF-8 es_ES.UTF-8 fr_FR.UTF-8 it_IT.UTF-8 km_KH sv_SE.UTF-8 fi_FI.UTF-8

RUN a2enmod rewrite expires

# Configure PHP
ADD custom.php.ini /etc/php/7.0/apache2/conf.d/

# Configure vhost
ADD custom.default.conf /etc/apache2/sites-enabled/000-default.conf

EXPOSE 80 443

WORKDIR /var/www

# RUN rm index.html

CMD ["apache2ctl", "-D", "FOREGROUND"]