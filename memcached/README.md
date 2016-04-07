qiscus/memcached
===

run from official memcached docker images

```
docker run -it \
	-p 11211:11211 \
	-d memcached \
	memcached -m 1024 -p 11211 -u memcache -l 0.0.0.0 -c 1024
```