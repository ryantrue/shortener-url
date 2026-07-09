# shortener-url

Simple URL shortener written in Go.

This project implements a minimal HTTP API for creating short links and resolving them back to original URLs. It is a compact educational backend service that can be used as a base for containerization, CI/CD practice and infrastructure deployment examples.

## Tech stack

- Go 1.20
- Gin HTTP framework
- In-memory storage
- Environment-based configuration

## Features

- Create a short URL from a full URL
- Resolve a short URL by identifier
- Configurable server address
- Configurable base URL
- Simple internal service structure

## API

### Create short URL

```http
POST /
Content-Type: text/plain

https://example.com/some/long/url
```

Response example:

```text
http://localhost:8080/1a2b3c4d
```

### Resolve short URL

```http
GET /:id
```

Example:

```bash
curl -i http://localhost:8080/1a2b3c4d
```

## Configuration

The service supports command-line flags and environment variables.

### Environment variables

```env
SERVER_ADDRESS=:8080
BASE_URL=http://localhost:8080
```

### Flags

```bash
-a :8080
-b http://localhost:8080
```

## Run locally

```bash
go run ./cmd/shortener
```

With custom configuration:

```bash
SERVER_ADDRESS=:8080 BASE_URL=http://localhost:8080 go run ./cmd/shortener
```

## Build

```bash
go build -o shortener ./cmd/shortener
```

Run binary:

```bash
./shortener
```

## Project structure

```text
cmd/shortener/              # Application entrypoint
internal/common/config/     # Configuration
internal/common/server/     # HTTP server and routes
internal/common/storage/    # URL storage service
```

## Current limitations

- Storage is in-memory only
- Data is lost after restart
- No authentication
- No persistent database yet
- No Dockerfile yet
- No CI pipeline yet

## DevOps improvement roadmap

- Add Dockerfile
- Add `docker-compose.yml`
- Add GitHub Actions pipeline
- Add tests to CI
- Add PostgreSQL or Redis storage
- Add healthcheck endpoint
- Add Prometheus metrics
- Add deployment example for Docker Compose or Kubernetes

## Why this repository matters

For a DevOps portfolio, this project can be used as a small service for demonstrating:

- container image build
- environment configuration
- CI/CD pipeline
- service deployment
- observability basics
- reverse proxy routing
- database migration from in-memory storage to persistent storage
