# go-next

Monorepo bootstrap for Go API + Next.js Web.

## Structure

- `apps/api`: Go API (Clean Architecture skeleton)
- `apps/web`: Next.js app (`src/app` based skeleton)
- `packages/contracts`: OpenAPI contract
- `docs`: Project documents
- `docker`: Container definitions

## Quick Start

1. Copy env template
2. Run `docker compose up --build`
3. Open:
   - Web: `http://localhost:3000`
   - API health: `http://localhost:8080/api/v1/health`
   - MinIO: `http://localhost:9011`
