# Gas Tank NHL snapshots

Public recommendation snapshots used by the existing NHL screen at https://www.gastanksports.com/?saved=1&sport=NHL.

The existing Vercel project dispatches this workflow every 15 minutes, at UTC minutes 09, 24, 39 and 54. Each run uses the private Gas Tank engine, official NHL statistics and the free PropLine feed. Only the public recommendation snapshot is committed here. Application source, raw odds feeds, API keys and private research records are not published.

Standard hosted Actions jobs in this public repository are free. A read-only, repository-scoped deploy key reads the private engine; the workflow token can write only this snapshot repository. No database is resumed and no paid fallback is configured.

The website checks for new snapshots automatically. Prices are timestamped observations and can move between updates. Picks stop being actionable at game time or when the snapshot expires. These are analytical recommendations, not placed bets or guaranteed results.

GitHub native scheduling is disabled to prevent duplicate scans. The first automatic Vercel-triggered publication succeeded on October 23, 2026 at 15:25 UTC.
