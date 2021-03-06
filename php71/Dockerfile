#-------------------------------------------------------------------------------------
# PhpProject - PHP 7.1
#-------------------------------------------------------------------------------------

FROM ubuntu:bionic

# Corrige alguns problemas estranhos do terminal, 
# como problemas como 'clear' ou CTRL+L
ENV TERM=linux

# Para o apt não fazer perguntas ao instalar pacotes
ENV DEBIAN_FRONTEND=noninteractive

# Configuração dos repositórios do Ondrej para Ubuntu Bionic, 
# instalação do PHP e ferramentas úteis
RUN apt-get update \
    && apt-get install -y --no-install-recommends gnupg \
    && echo "deb http://ppa.launchpad.net/ondrej/php/ubuntu bionic main" > /etc/apt/sources.list.d/ondrej-php.list \
    && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4F4EA0AAE5267A6C \
    && apt-get update \
    && apt-get -y --no-install-recommends install \
        ca-certificates \
        curl \
        unzip \
        php-apcu \
        php-apcu-bc \
        php7.1-cli \
	    php7.1-fpm \
	    php7.1-bcmath \
        php7.1-bz2 \
        php7.1-calendar \
        php7.1-curl \
        php7.1-dba \
        php7.1-enchant \
        php7.1-exif \
        php7.1-gd \
        php-gearman \
        php-igbinary \
        php-imagick \
        php7.1-imap \
        php7.1-interbase \
        php7.1-intl \
        php7.1-gmp \
        php7.1-json \
        php7.1-ldap \
        php7.1-mbstring \
        php-memcached \
        php7.1-mysql \
        php-mongodb \
        php-msgpack \
        php7.1-odbc \
        php7.1-opcache \
        php7.1-pgsql \
        php7.1-phpdbg \
        php7.1-pspell \
        php-raphf \
        php7.1-readline \
        php7.1-recode \
        php-redis \
        php7.1-soap \
        php7.1-sqlite3 \ 
        php-ssh2 \
        php7.1-sybase \
        php-tideways \
        php7.1-tidy \
        php-xdebug \
        php7.1-xml \
        php7.1-xmlrpc \
        php7.1-xsl \
        php-yaml \
        php-zmq \
        php7.1-zip \
        php7.1-mysql \
        git \
        vim \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer clear-cache \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/* ~/.composer

STOPSIGNAL SIGQUIT

# Adaptações para funcionar no docker
ADD https://raw.githubusercontent.com/ricardopedias/php-project-images/master/php71/overrides.conf /etc/php/7.1/fpm/pool.d/z-overrides.conf

CMD ["/usr/sbin/php-fpm7.1", "-O" ]

EXPOSE 9000


