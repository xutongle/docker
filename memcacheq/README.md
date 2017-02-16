MemcacheQ - Simple Queue Service over Memcache
---

![](https://img.shields.io/badge/MemcacheQ-0.2.0-brightgreen.svg) ![](https://img.shields.io/badge/Debian-jessie-brightgreen.svg) ![](https://img.shields.io/docker/stars/xutongle/memcacheq.svg) ![](https://img.shields.io/docker/pulls/xutongle/memcacheq.svg)

detail : [http://memcachedb.org/memcacheq/](http://memcachedb.org/memcacheq/)

#### Volume

- /var/lib/memcacheq

#### Custom usage:

    docker run \
        -d \
        --name memcacheq \
        -p 22201:22201 \
        -v /local_path/memcacheq:/var/lib/memcacheq:rw \
        xutongle/memcacheq

#### Compose example:

    memcacheq:
      image: xutongle/memcacheq
      ports:
        - "22201:22201"
      volumes:
        - /local_path/memcacheq:/var/lib/memcacheq:rw
      restart: always

