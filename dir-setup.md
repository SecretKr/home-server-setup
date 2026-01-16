# Create the main data folder on your SSD

```
sudo mkdir -p /data/storage
sudo mkdir -p /data/torrents
```

# Create folders for container configurations

```
mkdir -p ./docker/homer/assets
mkdir -p ~/docker/portainer
mkdir -p ~/docker/homebridge
mkdir -p ~/docker/qbittorrent/config
mkdir -p ~/docker/scrutiny/config
mkdir -p ~/docker/scrutiny/influxdb
mkdir -p ~/docker/jellyfin/config
```

# Set permissions so containers can write to the storage

```
sudo chmod -R 777 /data
```
