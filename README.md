# compose-mirandaclinics

This repository contains four separate Docker Compose stacks for the Miranda Clinics services.

## Clone on a server

Run the following commands on your server CLI to clone the repository and enter the project folder:

```bash
git clone https://github.com/solcredio-admin/miranda-clinics-compose.git
cd miranda-clinics-compose
```

## Requirements

Make sure Docker is installed and running on your machine.

- Docker Desktop on macOS, or
- Docker Engine with the Compose plugin

## Start each service step by step

From the repository root, open a terminal and run the following commands one by one.

### 1) API

```bash
cd miranda-clinics-api
docker compose pull
docker compose up -d
```

### 2) Control

```bash
cd ../miranda-clinics-control
docker compose pull
docker compose up -d
```

### 3) Queue

```bash
cd ../miranda-clinics-queue
docker compose pull
docker compose up -d
```

### 4) Web

```bash
cd ../miranda-clinics-web
docker compose pull
docker compose up -d
```

## Access points

After startup, the services should be available at:

- API: http://localhost:432
- Control: http://localhost:956
- Queue: http://localhost:765
- Web: http://localhost:631

## Stop the services

To stop them later, run the same commands with `down` in each directory:

```bash
cd miranda-clinics-api
docker compose down
```

Repeat the same pattern for the other three folders.

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
