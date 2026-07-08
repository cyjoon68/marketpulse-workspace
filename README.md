# MarketPulse Workspace

Public portfolio workspace for a Frontend / Product Engineer application.

## Repository topology

- Organization workspace: `https://github.com/marketpulse-labs/marketpulse-workspace`
- Personal mirror: `https://github.com/cyjoon68/marketpulse-workspace`
- App submodule: `https://github.com/marketpulse-labs/marketpulse-fe`
- API submodule: `https://github.com/marketpulse-labs/marketpulse-be`
- Default branch: `develop`
- `main` branch is retained.

## Implementation scope

- FE: React, TypeScript, `ky`, TanStack Query, D3, jQuery/Ajax compatibility, Playwright smoke test.
- BE: Python Flask RESTful API, module, PostgreSQL, Tortoise ORM, pytest, OpenAPI, k6.
- demo-backend conversion: auth/user/phone/token ideas converted to REST. GraphQL is not used.

## Local commands

```bash
git submodule update --init --recursive
cd marketpulse-fe && npm install && npm run build
cd ../marketpulse-be && python -m venv .venv && . .venv/bin/activate && pip install -r requirements.txt && pytest
```

## Screenshot

![MarketPulse dashboard](docs/screenshots/dashboard.png)

## API example

```http
GET /api/dashboard
PATCH /api/events/{event_id}/status
POST /api/auth/refresh
```

## ERD

```mermaid
erDiagram
  users ||--o{ refresh_tokens : owns
  products ||--o{ price_snapshots : records
  products ||--o{ inventory_snapshots : records
  products ||--o{ product_events : emits
```

## Verification

- `npm install && npm run build`: passed
- `npm audit --audit-level=critical`: passed, 0 vulnerabilities
- `npm run test:e2e`: passed, 1 Playwright smoke test
- `pip install -r requirements.txt && pytest`: passed, 2 tests
- Screenshot captured with Playwright
