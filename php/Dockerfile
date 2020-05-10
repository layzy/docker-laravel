FROM amazonlinux:2

# nginxとphpのインストール
RUN yum -y update && \
    amazon-linux-extras install -y php7.4 && \
    yum install -y php-mbstring 

# xdebugのインストール
RUN yum -y install php-pear php-devel gcc make && \
    pecl install xdebug

# composerのインストール
RUN php -r "readfile('https://getcomposer.org/installer');" > composer-setup.php && \
    php composer-setup.php --filename=composer&& \
    php -r "unlink('composer-setup.php');" && \
    mv composer /usr/local/bin/composer

# supervisorのインストール
RUN yum install -y python3 && pip3 install supervisor

COPY ./files/xdebug.ini /etc/php.d/xdebug.ini
COPY ./files/www.conf /etc/php-fpm.d/www.conf

EXPOSE 9000

ENTRYPOINT ["php-fpm", "-F"]