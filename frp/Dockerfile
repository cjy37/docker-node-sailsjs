FROM alpine:3.7
MAINTAINER rocky <75264521@qq.com>

ARG FRP_VERSION=0.20.0

WORKDIR /tmp
RUN set -x \
    && wget https://github.com/fatedier/frp/releases/download/v${FRP_VERSION}/frp_${FRP_VERSION}_linux_amd64.tar.gz \
    && tar -zxf frp_${FRP_VERSION}_linux_amd64.tar.gz \
    && mv frp_${FRP_VERSION}_linux_amd64 /var/frp \
    && mkdir -p /var/frp/conf

COPY conf/frps.ini /var/frp/conf/frps.ini

# conf被配置成了卷，方便以后修改frps.ini
VOLUME /var/frp/conf    

WORKDIR /var/frp

EXPOSE 7000 7500 80 443

ENTRYPOINT ./frps -c ./conf/frps.ini