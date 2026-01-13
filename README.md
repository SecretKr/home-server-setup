# Home Server User Manual

**Server IP Address:** `192.168.1.XXX` (Replace with your actual IP)  
**Host Name:** `homeserver`

---

## 🚀 Quick Access Reference

| Service         | Port/Address             | Description                     |
| :-------------- | :----------------------- | :------------------------------ |
| **Portainer**   | `http://<IP>:9000`       | Server Management Dashboard     |
| **qBittorrent** | `http://<IP>:8080`       | Torrent Downloader              |
| **Plex**        | `http://<IP>:32400/web`  | Media Streaming (Netflix-style) |
| **Samba (NAS)** | `\\<IP>` or `smb://<IP>` | File Access (Windows/Mac)       |
| **Scrutiny**    | `http://<IP>:8081`       | SSD/Hard Drive Health           |
| **Homebridge**  | `http://<IP>:8581`       | Smart Home Integration          |
| **Tailscale**   | _(App Based)_            | Remote VPN Access               |

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

## 2. qBittorrent (Downloader)

**How to download movies/software.**

- **URL:** `http://<SERVER-IP>:8080`
- **Default Login:** `admin` / `adminadmin` (Please change this in Settings!)

### ⚡ Important Settings

- **Save Path:** Always ensure downloads go to `/downloads/`.
- **Automation:** Anything downloaded here automatically appears in the **NAS "Torrents" folder** and is visible in **Plex**.

---

## 3. Plex Media Server

**How to watch your content.**

- **URL:** `http://<SERVER-IP>:32400/web`
- **Apps:** Download the Plex app on your Smart TV, Phone, or Tablet.

### 🎥 How it works

1. Download a movie via **qBittorrent**.
2. Wait for the download to finish.
3. Open **Plex**.
4. Plex will automatically scan the folder, add the poster/metadata, and let you stream it.

---

## 4. Portainer (Server Manager)

**The control center for the system.**

- **URL:** `http://<SERVER-IP>:9000`

### 🛠️ Usage

- Go here to **Restart** containers if they crash.
- View **Logs** to see why something isn't working.
- **Warning:** Do not delete containers here unless you know what you are doing.

---

## 5. Homebridge

**Smart Home Integration.**

- **URL:** `http://<SERVER-IP>:8581`
- **Default Login:** `admin` / `admin`

### 🏠 Usage

1. Log in to the web interface.
2. Install plugins for your smart devices (Tuya, Nest, Ring, etc.).
3. Scan the **QR Code** on the dashboard using your iPhone's **Home App**.
4. Your non-Apple devices now work with Siri/HomeKit.

---

## 6. Scrutiny

**Hard Drive Health Monitor.**

- **URL:** `http://<SERVER-IP>:8081`

### 🩺 Usage

- Check this periodically.
- Look for the **Status** column. It should say **PASS**.
- If you see **FAIL** or red warnings, your SSD might be failing—backup your data immediately.

---

## 7. Tailscale

**Remote Access (VPN).**

### 🌍 How to access from outside home

1. Download the **Tailscale App** on your phone or laptop.
2. Log in with the same account you used to set up the server.
3. Turn the VPN switch **ON**.
4. You can now access all the services (Plex, Sonarr, NAS) as if you were sitting at home on your WiFi.

---

## 🔧 Troubleshooting / Common Commands

If you need to fix something via SSH (Terminal), here are the cheat codes.

**1. Update the Server**

```bash
sudo apt update && sudo apt upgrade -y
```
