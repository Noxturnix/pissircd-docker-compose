# unrealircd-docker-compose

Docker (compose) for unrealircd

## How to use

Create `unrealircd.conf`, `server.cert.pem`, and `server.key.pem` in `config/`. You can get an example of unrealircd.conf [here](https://raw.githubusercontent.com/unrealircd/unrealircd/unreal52/doc/conf/examples/example.conf). You can edit [docker-compose.yml](docker-compose.yml) to suit your settings.

After that, just run

```
sudo docker-compose up -d
```

To stop your ircd, run

```
sudo docker-compose down
```

# License

[Unlicense](LICENSE)
