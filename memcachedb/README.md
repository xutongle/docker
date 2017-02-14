MemcacheDB - A distributed key-value storage system designed for persistent.
---

detail : [http://memcachedb.org/](http://memcachedb.org/)

**Version**

*1.2.1*     [Dockerfile](https://github.com/xutongle/docker/memcachedb/blob/master/Dockerfile)


*latest*    [Dockerfile](https://github.com/xutongle/docker/memcachedb/blob/master/Dockerfile)

**Usage**

    docker run -d -p 21211:21211 --name memcachedb xutongle/memcachedb:1.2.1
  
**Store Data**

    docker run -d -p 21211:21211 --name memcachedb -v /my-data-dir:/var/lib/memcachedb xutongle/memcachedb:1.2.1
  
  
