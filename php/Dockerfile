FROM amazonlinux:2

# phpのインストール
RUN yum -y update && \
    amazon-linux-extras install -y php7.4 && \
    yum install -y php-mbstring unzip tar

# xdebugのインストール
RUN yum -y install php-pear php-devel gcc make && \
    pecl install xdebug

# composerのインストール
RUN php -r "readfile('https://getcomposer.org/installer');" > composer-setup.php && \
    php composer-setup.php --filename=composer&& \
    php -r "unlink('composer-setup.php');" && \
    mv composer /usr/local/bin/composer

# nodejsのインストール
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
RUN . ~/.nvm/nvm.sh && nvm install node && npm i -g yarn

# supervisorのインストール
RUN yum install -y python3 && pip3 install supervisor

COPY ./files/xdebug.ini /etc/php.d/xdebug.ini
COPY ./files/www.conf /etc/php-fpm.d/www.conf

EXPOSE 9000

ENTRYPOINT ["php-fpm", "-F"]