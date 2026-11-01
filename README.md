## 👋 Welcome to rsyslog 🚀

Centralized log collection server running syslog-ng

## 📋 Description

Centralized log collection server running syslog-ng

## 🚀 Services

- **app**: lscr.io/linuxserver/syslog-ng:latest

## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/rsyslog/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/rsyslog" ~/.local/srv/docker/rsyslog
cd ~/.local/srv/docker/rsyslog
cp default.env .env
docker compose --env-file .env up -d
```

### Option 3: Using composemgr
```bash
composemgr install rsyslog
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
APP_ORG_NAME=Syslog-ng
SERVICE_USER=0
SERVICE_GROUP=0
```

See `docker-compose.yaml` for complete list of configurable options.

### Environment Files

`default.env.sample` holds the full set of variables and is copied to `.env`
before starting the stack:

```bash
cp default.env .env
docker compose --env-file .env up -d
```

`app.env.sample` holds the app-specific overrides and is copied to `app.env`:

```bash
cp app.env.sample app.env
```

`composemgr up` applies `app.env` and `default.env` automatically. Raw
`docker compose` commands need `--env-file .env` to pick up the same values.

### Reverse Proxy

Three standalone compose files ship in this repo:

| File | Use |
|------|-----|
| `docker-compose.yaml` | Default, published on `172.17.0.1:64332` |
| `docker-compose.traefik.yaml` | Behind an existing external `traefik` network |
| `docker-compose.tunnel.yaml` | Behind an existing external `cloudflare` tunnel network |

```bash
docker compose -f docker-compose.traefik.yaml --env-file .env up -d
```

## 🌐 Access

- **Web Interface**: http://172.17.0.1:64332
- **Syslog (UDP)**: udp://172.17.0.1:5514
- **Syslog (TCP)**: tcp://172.17.0.1:6514
- **Syslog framing (TCP)**: tcp://172.17.0.1:6601

## 📂 Volumes

- `./volumes/data/log/rsyslog` - Collected log files
- `./volumes/config/rsyslog` - syslog-ng configuration
## 🔐 Security

- Change all default passwords before deploying to production
- Use strong secrets for all authentication tokens
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly
The syslog listeners are published unencrypted - restrict them with a host firewall
syslog-ng configuration is written to ./volumes/config/rsyslog/config

## 🔍 Logging

```shell
docker compose --env-file .env logs -f app
```

## 🛠️ Management

```bash
# Start services
docker compose --env-file .env up -d

# Stop services
docker compose --env-file .env down

# Update to latest images
docker compose --env-file .env pull && docker compose --env-file .env up -d

# View logs
docker compose --env-file .env logs -f

# Restart services
docker compose --env-file .env restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
