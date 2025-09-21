# Full-Stack Tasks (NestJS + React) — Docker @ 5235

**Stack:** NestJS (JWT + TypeORM + PostgreSQL) + React (Vite, Tailwind)  
**Port exposed:** `5235` (frontend). Backend runs inside Docker on `5236` and is proxied via `/api`.

## Run locally with Docker
```bash
cp .env.example .env
docker compose up --build -d
```

- Frontend: http://localhost:5235
- API (proxied): http://localhost:5235/api
- Inside network, backend is `http://backend:5236`

## Default user
Register a user via the UI or via API:
```bash
POST /auth/register { "email":"admin@admin.com", "password":"Admin123!" }
POST /auth/login { "email":"admin@admin.com", "password":"Admin123!" }
```

## Migrations
Migrations run automatically on container start. To generate new ones (locally):
```bash
# Inside backend container
docker compose exec backend npm run typeorm:generate -- src/migrations/AutoMigration
```

---
