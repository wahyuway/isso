# docker isso
Isso – is a lightweight alternative commenting server similar to Disqus

## Description:

This docker image based on a [isso](https://posativ.org/isso/) comments.

## Usage:
```
docker run --name bind -d -p 7000:8080 \
-v /config:/config" \
-v /db:/db" \
--restart=always wahyuway/isso
```

## Docker-compose:
``` 
version: '2.3'
services:
    isso:
        image: wahyuway/isso
        ports:
            - "7000:8080"
        volumes:
            - ./app/config:/config
            - ./app/db:/db
        restart: always 
```

```
docker-compose up -d
```

## Isso stuff

### Minimal isso.cfg
``` 
[general]
dbpath = /db/comments.db
host = https://example.tld/
[server]
listen = http://0.0.0.0:7000
```

### environment variable:

The image use an environment variable (``ISSO_SETTINGS``) to define the path to isso.cfg (see https://posativ.org/isso/docs/configuration/server/)

The default value of ``ISSO_SETTINGS`` is **/config/isso.cfg**

