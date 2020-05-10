# Dockerで始めるLaravel講座用docker-compose

## how to use

何処か適当なところに新しくディレクトリを切ってから、その配下で `git clone` してください。
cloneできたら、 `html` という作業用ディレクトリを作ってからcloneで作られたディレクトリに移動し、下記コマンドを実行してください。

```
$ docker-compose up -d
```

先程作成した `html` というディレクトリはnginx及びphpのコンテナの `/usr/share/nginx/html` にマウントされています。

