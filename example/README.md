This directory shows a minimal caddy setup using the cache-handler module.

The [Caddyfile](./Caddyfile) configures a file server that enables the cache
module via the initial

```
{
    cache
}
```

And then configure a [TTL](https://en.wikipedia.org/wiki/Time_to_live) duration
of 240 seconds via the 

```
    cache {
      ttl 240s
    }
```

under the configuration for port 80.

You can run the images we publish based on the [../Dockerfile](../Dockerfile) to
server the [./index.html](./index.html) with the Caddyfile configuration via

``` sh
docker run --rm -p 9191:80 \
  --mount type=bind,src=./Caddyfile,target=/etc/caddy/Caddyfile \
  --mount type=bind,src=./index.html,target=/usr/share/caddy/index.html \
  shonfeder/caddy-cache-handler
```

Navigate to <http://localhost:9191/> to see the result.
