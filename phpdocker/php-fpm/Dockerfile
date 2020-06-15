FROM phpdockerio/php73-fpm:latest
WORKDIR "/application"

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

# Install selected extensions and other stuff
RUN apt-get update \
    && apt-get -y --no-install-recommends install  php-memcached php7.3-mysql php7.3-pgsql php-redis php7.3-bcmath php7.3-gd php7.3-imap php-imagick php7.3-intl php7.3-soap php7.3-xmlrpc php7.3-ctype php7.3-fileinfo php7.3-json php7.3-mbstring openssl php7.3-pdo php7.3-tokenizer php7.3-xml php7.3-zip libxml2 php7.3-curl php7.3-common php7.3-cli php7.3-xsl php-yaml \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install git
RUN apt-get update \
    && apt-get -y install git \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*
