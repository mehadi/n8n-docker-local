# n8n Docker Setup Guide

This guide explains how to run n8n using Docker Compose.

## Prerequisites
- Docker installed ([Install Docker](https://docs.docker.com/get-docker/))
- Docker Compose (included with Docker Desktop)

## Running with Docker Compose

1. Start the service:
   ```bash
   docker-compose up -d
   ```

2. To stop:
   ```bash
   docker-compose down
   ```

## Configuration

### Environment Variables
You can configure n8n by modifying environment variables in the `docker-compose.yml` file:

| Variable | Description            | Default Value           |
|----------|------------------------|-------------------------|
| `N8N_RUNNERS_ENABLED` | Enable rnners          | `true`                  |
| `N8N_BASIC_AUTH_ACTIVE` | Enable or disable basic authentication for the n8n editor UI         | `true`                  |
| `N8N_EDITOR_BASE_URL` | Base URL for accessing the n8n editor         | `http://localhost:5678` |
| `N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS` | Enforce strict file permissions on settings | `true`                  |
| `N8N_OWNER` | Email of the owner account (replace with your real email)    | `admin@example.com` |

### Persistent Storage
Data is persisted in the `n8n_data` directory via Docker volume.

## Accessing n8n
After starting the container, access n8n at:
[http://localhost:5678](http://localhost:5678)

Use the credentials:
- **Username:** admin@example.com
- **Password:** Strongpass123

## Important Notes
1. **Change default credentials** in `docker-compose.yml` before deploying to production
2. The `n8n_data` volume preserves workflows and credentials between restarts
3. Container will automatically restart on failure due to `restart: always` policy