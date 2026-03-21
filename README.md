# Canopy Directory

The phonebook for the TreeOS network. A directory service that tracks registered Lands and their public Trees across the decentralized TreeOS ecosystem.

## What it does

- **Land registration** — Lands announce themselves to the directory with their domain, public key, and metadata
- **Public tree indexing** — Each land can publish public trees that are searchable across the network
- **Health monitoring** — Periodic health checks track land availability and mark unreachable lands
- **Dashboard** — A web UI at `/` showing registered lands, public trees, and network stats

## API

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | Web dashboard |
| `POST` | `/directory/register` | Register or update a land |
| `GET` | `/directory/lands` | List lands (supports `?q=`, `?status=`, `?page=`, `?limit=`) |
| `GET` | `/directory/land/:domain` | Get details for a single land |
| `GET` | `/directory/search/trees` | Search public trees (supports `?q=`, `?land=`, `?page=`, `?limit=`) |
| `DELETE` | `/directory/land/:domain` | Remove a land (requires auth) |
| `GET` | `/directory/health` | Service health check |

## Setup

```bash
cd directory
npm install
```

Copy `.env.example` and configure:

```bash
cp .env.example .env
```

Run:

```bash
npm start        # production
npm run dev      # development (auto-reload)
```

Requires MongoDB running locally (default: `mongodb://localhost:27017/canopy-directory`).

## Stack

- Node.js + Express
- MongoDB + Mongoose
- Server-rendered dashboard (no frontend framework)

## Links

- [TreeOS](https://treeos.ai)
- [What is a Land?](https://treeos.ai/about/land)
