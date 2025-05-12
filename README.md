# Directarr

Plex/Jellyfin, Arr-Suite, but with OCH? Automate it with **Directar**.
This Projekt use JDownloader as Download-Client and emulates a **TODO** in Sonarr/Radarr.

## 🚀 Features
- **Configurable** - Configure Directarr like you want to
- **Selfhost** - Self-Host it with Docker

## Installation
Install it with Docker:

compose.yaml
```yaml
services:
    directarr:
        image: ghcr.com/Stainless0201/directarr:latest
        container_name: directarr
        ports:
            - 3000:3000
```
Docker run
```bash
docker run --name directarr -p 3000:3000 ghcr.com/Stainless0201/directarr:latest
```
## Configuration
```yaml:
services:
    directarr:
        environment:
            debug: True
```
---
## 🌍 Community

- 🐛 Found a bug? Open an [Issue](https://github.com/Stainless0201/directarr/issues)


## 🧩 Roadmap

- [ ] API to Sonarr/Radarr
- [ ] API to JDownloader
- [ ] Get Requests from Sonarr/Radarr
- [ ] Web-Scrap OHC-Sites
- [ ] Web UI to Solve Captchas


## 📜 License

MIT — Free as in freedom and free as in coffee. ☕