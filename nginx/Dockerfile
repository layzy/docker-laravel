FROM amazonlinux:2

# nginxとphpのインストール
RUN yum -y update && \
    amazon-linux-extras install -y nginx1

COPY ./files/default.conf /etc/nginx/conf.d/default.conf
COPY ./files/nginx.conf /etc/nginx/nginx.conf

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]