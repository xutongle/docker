FROM xutongle/dependent:latest

ENV DEBIAN_FRONTEND noninteractive

MAINTAINER XUTONGLE <xutongle@gmail.com>

WORKDIR /tmp

RUN wget -c --no-check-certificate https://xutl.oss-cn-hangzhou.aliyuncs.com/docker-asset/vlmcs/vlmcsdmulti-x64-musl-static && \
    mv vlmcsdmulti-x64-musl-static /usr/local/bin/vlmcsd && \
    chmod 755 /usr/local/bin/vlmcsd

EXPOSE 1688

# Define the default command.
CMD ["/usr/local/bin/vlmcsd","-f"]
#CMD ["/bin/bash"]