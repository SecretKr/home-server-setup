# Home Server

**Host:** `home-server` | **OS:** Debian/Ubuntu | **Storage:** `/data`

---

## 🚀 Services Links

| Service         | Address                   | Purpose                     |
| :-------------- | :------------------------ | :-------------------------- |
| **Homer**       | `http://<IP>:81`          | Dashboard                   |
| **qBittorrent** | `http://<IP>:8080`        | Downloads                   |
| **Jellyfin**    | `http://<IP>:8096`        | Media Streaming             |
| **Samba**       | `\\<IP>`                  | File Access                 |
| **Portainer**   | `http://<IP>:9000`        | Docker Management           |
| **Scrutiny**    | `http://<IP>:8081`        | HDD Health                  |
| **Homebridge**  | `http://<IP>:8581`        | Smart Home                  |

---

## 🛠️ Setup & Deployment

### 1. Initialize Folders
Create storage and configuration paths.
```bash
# Data volumes
sudo mkdir -p /data/{storage,torrents} && sudo chmod -R 777 /data

# Container Persistence
mkdir -p ~/home-server-data/{portainer,homebridge,qbittorrent/config,scrutiny/config,scrutiny/influxdb,jellyfin/config}
```

### 2. Configure & Deploy
```bash
cp .env.template .env
docker compose up -d
```

### 3. Caddy Reverse Proxy
```bash
# Install Caddy
sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | sudo gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.list' | sudo tee /etc/apt/sources.list.d/caddy-stable.list
sudo apt update && sudo apt install caddy

# Load Config
sudo cp ./configs/caddy/Caddyfile /etc/caddy/Caddyfile
sudo systemctl restart caddy
```

---

## 📂 File Sharing (Samba)
- **Windows**: Map network drive to `\\<IP>\HomeServer`
- **Mac**: Connect to Server (`Cmd+K`) `smb://<IP>`
- **User**: `user` | **Password**: (Defined in `.env`)

---

## 🔧 Maintenance

### Docker Management
- **Update Images**: `docker compose pull && docker compose up -d`
- **Resource Usage**: `docker stats`
- **Cleanup Disk**: `docker system prune -a --volumes` (Careful: removes unused data)
- **View Logs**: `docker compose logs -f [service]`

### System Health
- **Check Disk Space**: `df -h`
- **Check Folder Size**: `du -sh /data/*`
- **Real-time Monitor**: `htop` (Install with `sudo apt install htop`)

### Network
- **Check IP Address**: `hostname -I`
- **Test Caddy Config**: `caddy validate --config ./configs/caddy/Caddyfile`
