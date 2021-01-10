# Caddy-Trojan

## Build with xcaddy
```
$ xcaddy build \
    --with github.com/imgk/caddy-trojan-go/handler \
    --with github.com/imgk/caddy-trojan-go/listerner
```

## Config
```
{
    "apps": {
        "http": {
            "servers": {
                "": {
                    "listener_wrappers": [{
                        "wrapper": "trojan",
                        "trojan": {
                            "users": ["user-1", "user-2"],
                            "redis": {
                                "addr": "",
                                "password": "",
                                "db": 0
                            }
                        }
                    }],
                    "allow_h2c": true,
                    "routes": [
                        {
                            "handle": [
                                {
                                    "handler": "trojan",
                                    "trojan": {
                                        "users": ["user-1", "user-2"],
                                        "redis": {
                                            "addr": "",
                                            "password": "",
                                            "db": 0
                                        }
                                    }
                                }
                            ]
                        }
                    ]
                }
            }
        }
    }
}

```
