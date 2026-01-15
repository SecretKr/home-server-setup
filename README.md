# Home Server User Manual

**Host Name:** `home-server`

---

## 🚀 Quick Access Reference

| Service         | Port/Address             | Description                 |
| :-------------- | :----------------------- | :-------------------------- |
| **Homer**       | `http://<IP>:80`         | Dashboard                   |
| **qBittorrent** | `http://<IP>:8080`       | Torrent Downloader          |
| **Scrutiny**    | `http://<IP>:8081`       | SSD/Hard Drive Health       |
| **Jellyfin**    | `http://<IP>:8096`       | Media Streaming             |
| **Homebridge**  | `http://<IP>:8581`       | Smart Home Integration      |
| **Portainer**   | `http://<IP>:9000`       | Server Management Dashboard |
| **Samba (NAS)** | `\\<IP>` or `smb://<IP>` | File Access (Windows/Mac)   |
| **Tailscale**   | _(App Based)_            | Remote VPN Access           |

---

## 1. Samba NAS (File Sharing)

**How to access files from your computer.**

### 🖥️ Windows

1. Open File Explorer (`Win + E`).
2. In the address bar, type: `\\<SERVER-IP>`.
3. Press Enter.
4. **Login:**
   - User: `user`
   - Password: `mypassword` (or your custom password)

### 🍎 Mac

1. Open Finder.
2. Press `Command + K`.
3. Type: `smb://<SERVER-IP>`.
4. Click **Connect** and use the login details above.

### 📂 Shared Folders

- **Storage:** General purpose storage for documents/backups.
- **Torrents:** The destination for qBittorrent downloads and Plex media source.

---

## 🔧 Troubleshooting / Common Commands

If you need to fix something via SSH (Terminal), here are the cheat codes.

**1. Update the Server**

```bash
sudo apt update && sudo apt upgrade -y
```
