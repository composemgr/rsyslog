## 👋 Welcome to rsyslog 🚀

Self-hosted rsyslog application

## 📋 Description

Self-hosted rsyslog application

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
docker compose up -d
```

### Option 3: Using composemgr
```bash
composemgr install rsyslog
```

## 🔧 Configuration

### Environment Variables

```shell
SERVICE_USER=0
SERVICE_GROUP=0
TZ=America/New_York
```

See `docker-compose.yaml` for complete list of configurable options.

## 🌐 Access

- **Web Interface**: http://172.17.0.1:601

## 📂 Volumes

- `./rootfs/data/log/rsyslog` - Data storage
- `./rootfs/config/rsyslog` - Data storage

## 🔍 Logging

```shell
docker compose logs -f app
```

## 🛠️ Management

```bash
# Start services
docker compose up -d

# Stop services
docker compose down

# Update to latest images
docker compose pull && docker compose up -d

# View logs
docker compose logs -f

# Restart services
docker compose restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
