# Dockerで始めるLaravel講座用docker-compose

## how to use

何処か適当なところに新しくディレクトリを切ってから、その配下で `git clone` してください。
cloneできたら、 `html` という作業用ディレクトリを作ってからcloneで作られたディレクトリに移動し、下記コマンドを実行してください。

```
$ docker-compose up -d
```

先程作成した `html` というディレクトリはnginx及びphpのコンテナの `/usr/share/nginx/html` にマウントされています。

```
$ docker exec -it docker_php_1 bash
```

でphpのコンテナの中に入ってから `/usr/share/nginx/html` に移動して `app` という名前でLaravelプロジェクトを立ち上げると `http://localhost:8080` でLaravelの初期画面が表示できるようになると思います。

## 構成

* PHP7.4(php-fpm)
* nginx
* maria DB
* mailcatcher

## PHPコンテナに入れてあるもの

PHPコンテナというものの、PHPだけ入っているわけではないです。
Laravel開発やる上にあたって必要そうなの入れてます。

* PHP7.4
    * xdebug
        * php-fpmの通信ポートとの兼ね合いで、リモートポートを9001にしています
    * composer
* nodejs（多分最新）
* python3
    * supervisor使いたくなったときのため

参考： [Docker初心者がAmazon Linux2を前提にNginxとPHP-FPMの開発環境を整えてみた](https://qiita.com/tomitoshi/items/e9298f402c01f51dedab)