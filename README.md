# miranda-clinics-compose

This repository contains four separate Docker Compose stacks for the Miranda Clinics services.

## Requirements

**Docker must be installed and running on your machine.**

- Docker Desktop on macOS, or
- Docker Engine with the Compose plugin
- Installation guide: https://docs.docker.com/engine/install/ubuntu/

## Quick start

Run this single command to clone, enter the folder, and start all services:

```bash
git clone https://github.com/solcredio-admin/miranda-clinics-compose.git && cd miranda-clinics-compose && docker compose pull && docker compose up -d
```

## Access points

After startup, the services should be available at:

- API: http://localhost:432
- Control: http://localhost:956
- Queue: http://localhost:765
- Web: http://localhost:631

## Stop the services

To stop everything later, run:

```bash
docker compose down
```

## Caddyfile snippet

Paste the following into your Caddyfile if you want to expose the services through a single reverse proxy:

```caddy
api.example.com {
    reverse_proxy localhost:432
}

control.example.com {
    reverse_proxy localhost:956
}

queue.example.com {
    reverse_proxy localhost:765
}

www.example.com {
    reverse_proxy localhost:631
}
```

Replace the example domains with your real domain names.
