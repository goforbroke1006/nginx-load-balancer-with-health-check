FROM debian:jessie

MAINTAINER Sergey Cherkesov <go.for.broke1006@gmail.com>

RUN apt-get update
RUN apt-get install -y wget git

RUN cd /tmp && git clone --depth 1 --single-branch --branch master https://github.com/yaoweibin/nginx_upstream_check_module.git

RUN cd /tmp && wget 'http://nginx.org/download/nginx-1.14.2.tar.gz'
RUN cd /tmp && tar -xzvf nginx-1.14.2.tar.gz

RUN mv /tmp/nginx-1.14.2 /tmp/nginx-source

RUN cd /tmp/nginx-source && ls -lah ./src/http/modules/
RUN ls -lah /tmp/nginx_upstream_check_module

RUN cd /tmp/nginx-source && patch -f -p1 < /tmp/nginx_upstream_check_module/check_1.14.0+.patch

RUN apt-get install -y build-essential
RUN apt-get install -y libpcre++-dev
RUN apt-get install -y zlib1g-dev

RUN cd /tmp/nginx-source && ./configure --add-module=/tmp/nginx_upstream_check_module

RUN cd /tmp/nginx-source && make
RUN cd /tmp/nginx-source && make install

RUN /usr/local/nginx/sbin/nginx -v

EXPOSE 80

CMD ["/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]
