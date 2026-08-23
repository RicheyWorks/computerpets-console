# Console contract

Do not implement against folklore. Implement against this file.

## Identity

- Product: **Console**
- Repo: `computerpets-console`
- Category: Web & Client
- Idea: Admin Console
- Port / surface: `8080`

## Must

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

## Data

Operator(role) · Freeze(userId, reason, until) · SteamTicket(id, status)

## Surface

- GET /admin/users — search, flags, Steam id
- POST /admin/users/{id}/freeze — halt trades + overlay cloud sync
- GET /admin/steam/sync — ticket backlog
- GET /admin/economy/anomalies — ledger alerts

## Neighbors

- computerpets Spring backend
- computerpets-steamgate
- computerpets-ledger
- computerpets-telemetry
- computerpets-bounty

## Failure doctrine

Missing admin role → 403, empty shell. Steam outage → show stale with banner. Accidental freeze → 15-minute undo window.

## Stack

TypeScript · React 19 · Vite · Spring Boot admin API · Steam sync status · RBAC
