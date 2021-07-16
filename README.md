# unrealircd-docker-compose

Docker (compose) for unrealircd

## Setup

Create `unrealircd.conf`, `server.cert.pem`, and `server.key.pem` in `config/`. You can get an example of unrealircd.conf [here](https://raw.githubusercontent.com/unrealircd/unrealircd/unreal52/doc/conf/examples/example.conf). `openssl` can be used to create a self-signed certificate

```
openssl req -newkey rsa:4096 -nodes -keyout server.key.pem -x509 -days 365 -out server.cert.pem
```

You can edit [docker-compose.yml](docker-compose.yml) to suit your settings.

## Usages

Just run

```
sudo docker-compose up -d
```

To stop your ircd, run

```
sudo docker-compose down
```

# License

[Unlicense](LICENSE)
