MemcacheDB - A distributed key-value storage system designed for persistent.
---

![](https://img.shields.io/badge/MemcacheDB-1.2.1-brightgreen.svg) ![](https://img.shields.io/badge/Debian-jessie-brightgreen.svg) ![](https://img.shields.io/docker/stars/xutongle/memcachedb.svg) ![](https://img.shields.io/docker/pulls/xutongle/memcachedb.svg)

detail : [http://memcachedb.org/](http://memcachedb.org/)

#### Volume

- /var/lib/memcachedb

#### Custom usage:

    docker run \
        -d \
        --name memcachedb \
        -p 21211:21211 \
        -v /local_path/memcachedb:/var/lib/memcachedb:rw \
        xutongle/memcachedb

#### Compose example:

    memcachedb:
      image: xutongle/memcachedb
      ports:
        - "21211:21211"
      volumes:
        - /local_path/memcachedb:/var/lib/memcachedb:rw
      restart: always

  
  
