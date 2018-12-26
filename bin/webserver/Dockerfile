FROM ubuntu:18.04
# Arguments pass from docker-compose.yml file in webserver section
ARG USER
ARG TZ

# Update index and packages
RUN apt update -y --fix-missing
RUN apt upgrade -y

# Install utilities
RUN apt install -y apt-utils \
                   nano \
                   wget \
                   dialog \
                   net-tools \
                   software-properties-common \
                   gnupg \
                   zip \
                   unzip \
                   git \
                   curl \
                   iputils-ping

# Configuration of timezone, tzdata is necesary for PHP
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN DEBIAN_FRONTEND=noninteractive apt install -y tzdata

# Install importants libraries
RUN apt install -y build-essential \
                   libmcrypt-dev \
                   libsqlite3-dev \
                   libsqlite3-0 \
                   zlib1g-dev \
                   libicu-dev \
                   libfreetype6-dev \
                   libpng-dev \
                   libapache2-mod-php

# PHP extensions
RUN apt install -y php \
                   php-fpm \
                   php-cli \
                   php-xmlrpc \
                   php-gd \
                   php-xml \
                   php-json \
                   php-mysql \
                   php-curl \
                   php-mbstring \
                   php-zip \
                   php-sqlite3

# Apache
RUN apt install -y apache2

# Letsencrypt
RUN add-apt-repository -y ppa:certbot/certbot
RUN apt install -y python-certbot-apache

# Configurations
RUN echo "ServerName 172.22.0.2" >> /etc/apache2/conf-available/fqdn.conf

# Enable apache modules
RUN a2enmod rewrite headers proxy proxy_http
RUN a2enconf fqdn
RUN service apache2 start
#RUN a2dissite 000-default.conf

# Add user
RUN useradd -ms /bin/bash $USER
USER $USER
WORKDIR /home/$USER

# Install composer with newuser
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('SHA384', 'composer-setup.php') === '93b54496392c062774670ac18b134c3b3a95e5a5e5c8f1a9f115f203b75bf9a129d5daa8ba6a13e2cc8a1da0806388a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"

# Install composer globally
USER root
RUN mv composer.phar /usr/local/bin/composer

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]