# NATS - Instalação

## Baixar o binário
```
bash# wget https://github.com/nats-io/nats-server/releases/download/v2.2.6/nats-server-v2.2.6-linux-amd64.tar.gz
bash# tar zxvf nats-server-v2.2.6-linux-amd64.tar.gz
bash# cd nats-server-v2.2.6-linux-amd64/
bash# cp -p nats-server /usr/sbin/
```

## Configurar o systemd
```
bash# cat <<EOF > /etc/systemd/system/nats-server.service
[Unit]
Description=NATS server

[Service]
ExecStart=/usr/sbin/nats-server -c /etc/nats/config.cfg
Restart=on-failure
StandardOutput=append:/var/log/nats/nats.log
StandardError=append:/var/log/nats/error.log

[Install]
WantedBy=multi-user.target
EOF
```

## Configurar o nats. Ativar mqtt. Rodar em localhost
```
bash# cat <<EOF > /etc/nats/config.cfg
listen: 127.0.0.1:4222

server_name: mqtt_demo
jetstream {
  store_dir: datastore
}
mqtt {
  listen: 127.0.0.1:1883
}
EOF
```

## Rodar o serviço
```
bash# systemctl stop nats-server
bash# systemctl start nats-server
```

# nats-bench - instalação

```
bash# git clone https://github.com/nats-io/nats.go.git
bash# cd nats.go/examples/nats-bench/
bash# go install main.go
bash# cp -p $HOME/go/bin/main /usb/bin/nats-bench
```

## exemplos
```
bash# nats-bench -np 1 -n 100000 -ms 16 foo
bash# nats-bench -np 1 -ns 1 -n 100000 -ms 16 foo
bash# nats-bench -np 1 -ns 5 -n 10000000 -ms 16 foo
```

# Fonte
https://docs.nats.io/nats-server/configuration/mqtt/mqtt_config
