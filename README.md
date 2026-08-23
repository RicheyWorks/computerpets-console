# Console

**Admin Console** — Secure dashboard for moderating users, economy, and Steam syncing.

Part of the [ComputerPets](https://github.com/RicheyWorks/computerpets) ecosystem. Index: [computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem).

> Status: **design scaffold**. This repository ships the contract, README, and layout so implementation can start without renaming the organ later.

## Why it exists

Operators, not players. Ban, freeze listings, replay a Steam ticket, and see whether the overlay fleet is healthy.

The flagship overlay already puts a living sticker on the real desktop (Rui first, 210 kinds). Console does not replace that. It is one organ.

## Stack

TypeScript · React 19 · Vite · Spring Boot admin API · Steam sync status · RBAC

GroupId / namespace: `com.enterprisepet.console`  
Default listen: `8080`

## Talks to

- computerpets Spring backend
- computerpets-steamgate
- computerpets-ledger
- computerpets-telemetry
- computerpets-bounty

## Contract

### Data

`Operator(role) · Freeze(userId, reason, until) · SteamTicket(id, status)`

### Surface

- GET /admin/users — search, flags, Steam id
- POST /admin/users/{id}/freeze — halt trades + overlay cloud sync
- GET /admin/steam/sync — ticket backlog
- GET /admin/economy/anomalies — ledger alerts

### Failure doctrine

Missing admin role → 403, empty shell. Steam outage → show stale with banner. Accidental freeze → 15-minute undo window.

## Layout

```
computerpets-console/
  README.md           this file
  LICENSE             MIT
  docs/CONTRACT.md    the same contract, frozen for implementers
  src/                implementation lands here
```

## Run (Windows)

PowerShell, from this folder, after the flagship helpers (Git, Node LTS 22+, JDK 21 as needed):

```powershell
cd app; npm install; npm run dev
```

You do not need this service to meet Rui. The [flagship start-here](https://github.com/RicheyWorks/computerpets/blob/main/docs/START-HERE.md) is still the first pet.

## Ecosystem

| Organ | Repo |
| --- | --- |
| Flagship desktop + Spring | [RicheyWorks/computerpets](https://github.com/RicheyWorks/computerpets) |
| This organ | [RicheyWorks/computerpets-console](https://github.com/RicheyWorks/computerpets-console) |
| Full map | [RicheyWorks/computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem) |

## License

MIT. See [LICENSE](LICENSE).

---

*Two hundred ten living kinds. Keep them so a line does not go quiet.*
