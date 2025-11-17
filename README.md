# Marzban-node

## Quick install
Install Marzban-node on your server using this command
```bash
sudo bash -c "$(curl -sL https://github.com/xmohammad1/Marzban-scripts/raw/master/marzban-node.sh)" @ install
```
Install Marzban-node on your server using this command with custom name:
```bash
sudo bash -c "$(curl -sL https://github.com/xmohammad1/Marzban-scripts/raw/master/marzban-node.sh)" @ install --name marzban-node2
```
Or you can only install this script (marzban-node command) on your server by using this command
```bash
sudo bash -c "$(curl -sL https://github.com/xmohammad1/Marzban-scripts/raw/master/marzban-node.sh)" @ install-script
```

Use `help` to view all commands:
```marzban-node help```


## Manual install
Read the setup guide here: https://xmohammad1.github.io/marzban/docs/marzban-node

## Run with Docker directly
If you prefer to run the container manually without the helper script or docker-compose, be sure to raise the file descriptor and process limits as recommended for the systemd service. The equivalent `docker run` command looks like this:

```bash
docker run -d --name marzban-node \
  --network host \
  --restart always \
  --ulimit nofile=500000:500000 \
  --ulimit nproc=50000 \
  -e SSL_CERT_FILE="/var/lib/marzban-node/ssl_cert.pem" \
  -e SSL_KEY_FILE="/var/lib/marzban-node/ssl_key.pem" \
  -v /var/lib/marzban-node:/var/lib/marzban-node \
  gozargah/marzban-node:latest
```

These `--ulimit` flags mirror the `LimitNOFILE=500000` and `LimitNPROC=50000` settings defined for the systemd unit.
