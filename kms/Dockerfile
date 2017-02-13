FROM xutongle/dependent:latest

ENV DEBIAN_FRONTEND noninteractive

MAINTAINER XUTONGLE <xutongle@gmail.com>

WORKDIR /tmp

RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/vlmcs/vlmcsdmulti-x64-musl-static && \
    cp vlmcsdmulti-x64-musl-static /usr/local/bin/vlmcsdmulti-x64-musl-static

EXPOSE 1688

# Define the default command.
CMD ["/usr/local/bin/vlmcsdmulti-x64-musl-static","vlmcsd"]
#CMD ["/run.sh"]