FROM debian:jessie

ENV DEBIAN_FRONTEND noninteractive

MAINTAINER Tongle Xu <xutongle@gmail.com>

ENV INSTALL_PREFIX="/usr" \
    CURL_VERSION=7.52.1 \
    LIBICONV_VERSION=1.15 \
    LIBMCRYPT_VERSION=2.5.8 \
    MHASH_VERSION=0.9.9.9 \
    MCRYPT_VERSION=2.6.8 \
    JEMALLOC_VERSION=4.4.0 \
    PCRE_VERSION=8.40 \
    LIBMEMCACHED_VERSION=1.0.18

ADD sources.list /etc/apt/sources.list

RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y ca-certificates wget gcc g++ make cmake autoconf patch bzip2 libbz2-dev \
    psmisc pkg-config sendmail openssl libssl-dev git subversion supervisor bison re2c apt-utils libxslt-dev \
    libxml2 libxml2-dev libedit-dev libjpeg-dev libpng12-dev libpng3 libfreetype6 libfreetype6-dev libsasl2-dev libevent-dev && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /tmp

# install curl
RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/curl/curl-${CURL_VERSION}.tar.gz && \
    tar xzf curl-${CURL_VERSION}.tar.gz && \
    cd curl-${CURL_VERSION} && \
    ./configure --prefix=${INSTALL_PREFIX} && \
    make && make install && \
    rm -rf /tmp/*

# install libiconv
RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/libiconv/libiconv-${LIBICONV_VERSION}.tar.gz && \
    tar xzf libiconv-${LIBICONV_VERSION}.tar.gz && \
    cd libiconv-${LIBICONV_VERSION} && \
    ./configure --prefix=${INSTALL_PREFIX} && \
    make && make install && \
    rm -rf /tmp/*

# install mhash
RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/mhash/mhash-${MHASH_VERSION}.tar.gz && \
    tar xzf mhash-${MHASH_VERSION}.tar.gz && \
    cd mhash-${MHASH_VERSION} && \
    ./configure --prefix=${INSTALL_PREFIX} && \
    make && make install && \
    rm -rf /tmp/*

# install libmcrypt
RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/mcrypt/libmcrypt-${LIBMCRYPT_VERSION}.tar.gz && \
    tar xzf libmcrypt-${LIBMCRYPT_VERSION}.tar.gz && \
    cd libmcrypt-${LIBMCRYPT_VERSION} && \
    ./configure --prefix=${INSTALL_PREFIX} && \
    make && make install && \
    ldconfig && \
    cd libltdl && \
    ./configure --prefix=${INSTALL_PREFIX} --enable-ltdl-install && \
    make && make install && \
    rm -rf /tmp/*

# install mcrypt
RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/mcrypt/mcrypt-${MCRYPT_VERSION}.tar.gz && \
    tar xzf mcrypt-${MCRYPT_VERSION}.tar.gz && \
    cd mcrypt-${MCRYPT_VERSION} && \
    ./configure --prefix=${INSTALL_PREFIX} && \
    make && make install && \
    rm -rf /tmp/*

# install icu
RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/icu/icu4c-58_2-src.tgz && \
    tar xzf icu4c-58_2-src.tgz && \
    cd icu/source && \
    ./configure --prefix=${INSTALL_PREFIX} && \
    make && make install && \
    rm -rf /tmp/*

# install pcre
RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/pcre/pcre-${PCRE_VERSION}.tar.gz && \
    tar xzf pcre-${PCRE_VERSION}.tar.gz && \
    cd pcre-${PCRE_VERSION} && \
    ./configure --prefix=${INSTALL_PREFIX} --enable-utf8 && \
    make && make install && \
    rm -rf /tmp/*

# install libmemcached
RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/libmemcached/libmemcached-${LIBMEMCACHED_VERSION}.tar.gz && \
    tar xzf libmemcached-$LIBMEMCACHED_VERSION.tar.gz && \
    cd libmemcached-$LIBMEMCACHED_VERSION && \
#    sed -i "s@lthread -pthread -pthreads@lthread -lpthread -pthreads@" ./configure && \
    ./configure --prefix=${INSTALL_PREFIX} && \
    make && make install && \
    rm -rf /tmp/*

# install jemalloc
# 查看jemalloc状态  lsof -n | grep jemalloc
RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/jemalloc/jemalloc-${JEMALLOC_VERSION}.tar.bz2 && \
    tar xjf jemalloc-${JEMALLOC_VERSION}.tar.bz2 && \
    cd jemalloc-${JEMALLOC_VERSION} && \
    ./configure --prefix=${INSTALL_PREFIX} && \
    make && make install && \
    rm -rf /tmp/*

ADD supervisord.conf /etc/supervisor/supervisord.conf

# Define the default command.
CMD ["/bin/bash"]

#CMD ["supervisord","-n"]