qiscus/solr
===

build

```
docker build -t qiscus/solr .
```

You will need `/opt` content to successfully run this images, including config & data

```
docker run -it \
	-p 8080:8080 \
	-v /opt:/opt \
	--restart=always \
	-d qiscus/solr
```