# どんなdockerイメージを利用して構築をするか
FROM php:7.4-apache


#ローカル開発用（docker compose対応）
COPY ./backend /var/www/html

WORKDIR /var/www/html
#デプロイ用
#COPY ./backend /var/www/html

# 設定ファイルをdockerコンテナ内のPHP、Apacheに読み込ませる
ADD php.ini /usr/local/etc/php/
ADD 000-default.conf /etc/apache2/sites-enabled/

# Composerのインストール
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer

# ミドルウェアインストール
RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
vim \
libpng-dev \
libpq-dev \
&& docker-php-ext-install pdo_mysql

EXPOSE 80
# Laravelで必要になるmodRewriteを有効化する
RUN mv /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled
RUN /bin/sh -c a2enmod rewrite
RUN chmod -R 777 storage bootstrap/cache
#ENTRYPOINT ["chmod", "-R", "777", "storage", "bootstrap/cache"]

