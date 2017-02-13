FROM xutongle/dependent:latest

ENV DEBIAN_FRONTEND noninteractive

MAINTAINER XUTONGLE <xutongle@gmail.com>

ENV INSTALL_DIR=/usr/local \
    SERVER_ADDR=0.0.0.0 \
    SERVER_PORT=8388 \
    PASSWORD="" \
    METHOD=aes-256-cfb \
    TIMEOUT=300 \
    DNS_ADDR=8.8.8.8 \
    DNS_ADDR_2=8.8.4.4 \
    SS_VERSION=2.6.3

RUN apt-get update && \
  apt-get install -y --no-install-recommends libev-dev libudns-dev && \
  rm -rf /var/lib/apt/lists/*

WORKDIR /tmp

RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/shadowsocks/shadowsocks-libev-${SS_VERSION}.tar.gz && \
    tar xzf shadowsocks-libev-${SS_VERSION}.tar.gz && \
    cd shadowsocks-libev-$SS_VERSION && \
    ./configure --prefix=$INSTALL_DIR  --disable-documentation && \
    make && \
    make install && \
    rm -rf /tmp/*

EXPOSE $SERVER_PORT
EXPOSE $SERVER_PORT/udp

# Define the default command.
# Override the host and port in the config file.
ADD entrypoint /
ENTRYPOINT ["/entrypoint"]
CMD ["-h"]