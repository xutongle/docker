FROM alpine:3.4

ENV DEBIAN_FRONTEND noninteractive

RUN set -xe && apk add --no-cache iptables ppp pptpd

COPY etc/pptpd.conf /etc/pptpd.conf
COPY etc/chap-secrets /etc/ppp/chap-secrets
COPY etc/pptpd-options /etc/ppp/pptpd-options
COPY entrypoint.sh /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
CMD ["pptpd", "--fg"]
