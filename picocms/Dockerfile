FROM php:7-apache

RUN apt-get update && apt-get install -y \
    git-core \
    zip \
    && rm -rf /var/lib/apt/lists/*

RUN curl -sSL https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
    php /usr/bin/composer create-project picocms/pico-composer .

COPY config.yml ./config/
RUN rm ./config/config.yml.template

RUN git clone https://github.com/picocms/pico-theme.git ./theme/default

RUN git clone https://github.com/PontusHorn/Pico-Tags.git ./plugins/picoplugin && \
    cp ./plugins/picoplugin/PicoTags.php ./plugins/PicoTags.php && \
    rm -r ./plugins/picoplugin && \
    git clone https://github.com/PhrozenByte/pico-file-prefixes.git ./plugins/picoplugin && \
    cp ./plugins/picoplugin/PicoFilePrefixes.php ./plugins/PicoFilePrefixes.php && \
    rm -rf ./plugins/picoplugin

EXPOSE 80
