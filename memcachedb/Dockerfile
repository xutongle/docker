FROM xutongle/dependent:latest

ENV DEBIAN_FRONTEND noninteractive

MAINTAINER XUTONGLE <xutongle@gmail.com>

ENV INSTALL_DIR=/usr/local \
    LIBEVENT_VERSION=2.0.22 \
    BERKELEYDB_VERSION=4.8.30 \
    MEMCACHEDB_VERSION=1.2.1-beta

RUN apt-get update && \
  apt-get install -y --no-install-recommends gcc wget make && \
  rm -rf /var/lib/apt/lists/*

WORKDIR /tmp

# install libevent
RUN wget -c --no-check-certificate https://github.com/libevent/libevent/releases/download/release-${LIBEVENT_VERSION}-stable/libevent-${LIBEVENT_VERSION}-stable.tar.gz && \
    tar zxf libevent-${LIBEVENT_VERSION}-stable.tar.gz && \
    cd libevent-${LIBEVENT_VERSION}-stable && \
    ./configure --prefix=/usr && \
    make && make install && \
    rm -rf /tmp/*

# install berkeley-db
RUN wget -c http://download.oracle.com/berkeley-db/db-${BERKELEYDB_VERSION}.tar.gz && \
    tar xzf db-${BERKELEYDB_VERSION}.tar.gz && \
    cd db-${BERKELEYDB_VERSION}/build_unix && \
    ../dist/configure --prefix=/usr && \
    make && make install && \
    rm -rf /tmp/*

# install memcachedb
RUN wget -c --no-check-certificate https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/memcachedb/memcachedb-${MEMCACHEDB_VERSION}.tar.gz && \
    tar xzf memcachedb-${MEMCACHEDB_VERSION}.tar.gz && \
    cd memcachedb-${MEMCACHEDB_VERSION} && \
    ./configure --help && \
    ./configure --with-bdb=/usr --prefix=${INSTALL_DIR}  --enable-threads && \
    make && make install && \
    rm -rf /tmp/*

RUN mkdir -p /var/lib/memcachedb

EXPOSE 22201

VOLUME ["/var/lib/memcachedb"]

CMD ["/usr/local/bin/memcachedb","-uroot","-H /var/lib/memcachedb"]