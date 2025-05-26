# Directarr

Plex/Jellyfin, Arr-Suite, but with OCH? Automate it with **Directar**.
This Projekt use JDownloader as Download-Client and emulates a **TODO** in Sonarr/Radarr.

## 🚀 Features
- **Configurable** - Highly configurable
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
            filter-dl: ddownload,rapidgator
            hoster: filmfx.org,serienfx.org
            waitToAutoSolve: 10m
            nf-discord: https://discord.com/api/webhooks/XXXXXXXXXXXXXXXXXXX/XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
            nf-notifiarr: 
            jdownloader-username: max
            jdownloader-password: musterpassword
            jdownloader-clientname: musterclient
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
- [ ] All-In-One Image (include jdownloader in docker package)

## Architektur

- docker
    - everything with *environment* variables
    - base image *alpine* to minimize size

- Backend
    - scrap DL-Sites and extract filecrypt (etc) links
    - filter on download-hoster
    - is built with c#
        - [HTML Agility Pack](https://html-agility-pack.net/)
    - api to sonarr/radarr
    - api to frontend
    - caching in sqlite/redis
    - solving captchas
        - manual in frontend (select by list wich captcha)
        - automaticly with deathbycaptcha
    - notifications
        - discord-webhook
        - mail
        - notifiarr
    
```mermaid
stateDiagram-v2
    radarr/sonarr --> Request
    Request --> Scrapping
    Scrapping --> radarr/sonarr
    
    radarr/sonarr --> DL-Links
    DL-Links --> JDownloader
    JDownloader --> radarr/sonarr

    radarr/sonarr --> Jellyfin/Plex/Emby
```

- Frontend
    - VueJS/Svelte as framework
    - Show settings
        - apikey
    - List with active captchas
        - detailed infos about: source, hoster, dl-hoster, ...
    - show usefull error messages

## 📜 License

MIT — Free as in freedom and free as in coffee. ☕