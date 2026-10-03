# Console

**A clearer operating view of ComputerPets.**

A planned operator dashboard for user moderation, economy alerts, and Steam synchronization status, with role-based access.

**Stage: design scaffold.** This checkout contains a design document and a source placeholder. The experience below is planned; there is no runnable app or integrated service yet.

[Status](#status) · [Planned experience](#planned-experience) · [Contributor quickstart](#contributor-quickstart) · [Service contract](docs/CONTRACT.md) · [Ecosystem map](https://github.com/RicheyWorks/computerpets-ecosystem)

## Status

| Available today | What you can inspect |
| --- | --- |
| [Service contract](docs/CONTRACT.md) | Intended behavior, boundaries, and planned dependencies. |
| [Source placeholder](src/console/index.ts) | Name metadata only; no package.json, app, or runtime is checked in. |
| [MIT license](LICENSE) | Licensing terms for the repository. |

Gameplay, endpoints, integration arrows, and failure handling on this page describe implementation targets. No build/test harness, CI workflow, or product screenshots are included in this scaffold.

## Planned experience

- GET /admin/users — search, flags, Steam id
- POST /admin/users/{id}/freeze — halt trades + overlay cloud sync
- GET /admin/steam/sync — ticket backlog
- GET /admin/economy/anomalies — ledger alerts

### Planned technology

TypeScript · React 19 · Vite · Spring Boot admin API · Steam sync status · RBAC

### Planned connections

These arrows show intended dependencies, rather than working integrations.

```mermaid
flowchart LR
  operator --> console
  console --> steamgate
  console --> ledger
  console --> bounty
```

## Contributor quickstart

With access to this private repository, Git and PowerShell are enough to review the scaffold:

```powershell
git clone https://github.com/RicheyWorks/computerpets-console.git
Set-Location computerpets-console
Get-Content docs/CONTRACT.md
Get-Content src/console/index.ts
```

Read [Service contract](docs/CONTRACT.md) before choosing implementation details. The commands above inspect the checked-in files; app installation, editor launch, and server startup become possible after a buildable project and entry point are added.

### First implementation target

**User search + freeze that halts Bazaar and Visitation. Undo window 15 minutes.**

You know it works when: Missing role: 403 empty shell. Steam outage: stale banner, no fake 'synced'.

Treat this as an acceptance target for a future implementation. Start with the documented slice, add the required project setup and focused tests, and update these instructions with commands that work from a fresh clone.

## Design boundaries

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

**Required failure behavior:**

Missing admin role → 403, empty shell. Steam outage → show stale with banner. Accidental freeze → 15-minute undo window.

## Ecosystem

- [computerpets](https://github.com/RicheyWorks/computerpets) Spring backend
- [computerpets-steamgate](https://github.com/RicheyWorks/computerpets-steamgate)
- [computerpets-ledger](https://github.com/RicheyWorks/computerpets-ledger)
- [computerpets-telemetry](https://github.com/RicheyWorks/computerpets-telemetry)
- [computerpets-bounty](https://github.com/RicheyWorks/computerpets-bounty)

Start with the [ComputerPets flagship](https://github.com/RicheyWorks/computerpets) for the desktop pet. This repository describes an optional extension; the [ecosystem map](https://github.com/RicheyWorks/computerpets-ecosystem) explains the broader plan.

## License

MIT. See [LICENSE](LICENSE).
