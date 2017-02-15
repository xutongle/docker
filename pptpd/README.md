![](https://img.shields.io/badge/PPTPServer-1.4.0-brightgreen.svg) ![](https://img.shields.io/badge/Alpine-3.4-brightgreen.svg) ![](https://img.shields.io/docker/stars/xutongle/pptpd.svg) ![](https://img.shields.io/docker/pulls/xutongle/pptpd.svg)

#### Volume

- /etc/ppp

#### Custom usage:

    docker run \
        -d \
        --name pptpd \
        --privileged \
        -p 1723:1723 \
        -v /local_path/chap-secrets:/etc/ppp/chap-secrets:ro \
        xutongle/pptpd

#### Compose example:

    pptpd:
      image: xutongle/pptpd
      ports:
        - "1723:1723"
      volumes:
        - ./local_path/chap-secrets:/etc/ppp/chap-secrets:ro
      privileged: true
      restart: always
