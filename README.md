# Gas Tank NHL snapshots

Public recommendation snapshots used by the existing NHL screen at https://www.gastanksports.com/?saved=1&sport=NHL.

The existing Vercel project dispatches this workflow every 15 minutes, at UTC minutes 09, 24, 39 and 54. Each run uses the private Gas Tank engine, official NHL statistics and the free PropLine feed. Only the public recommendation snapshot is committed here. Application source, raw odds feeds, API keys and private research records are not published.

Standard hosted Actions jobs in this public repository are free. A read-only, repository-scoped deploy key reads the private engine; the workflow token can write only this snapshot repository. No database is resumed and no paid fallback is configured.

The website checks for new snapshots automatically. Prices are timestamped observations and can move between updates. Picks stop being actionable at game time or when the snapshot expires. These are analytical recommendations, not placed bets or guaranteed results.

GitHub native scheduling is disabled to prevent duplicate scans. The first automatic Vercel-triggered publication succeeded on October 23, 2026 at 15:25 UTC.

## Official NHL feed recovery

New keyless NHL requests are spaced one second apart. Temporary rate limits and network errors have bounded backoff (at most two retries per URL and eight recovery retries per run); failed URLs are not repeatedly requested for every player market. Original sample and qualification checks still apply. Roster-verified player IDs are passed directly to game-log reads.

Successful public NHL JSON responses can be reused for up to one hour through the existing free Actions cache. Only the dedicated `nhl-official-json` directory is cached; private engine bundles, credentials, raw odds and research files are excluded. No cache storage increase or paid service is enabled.

Source health counters are logged after every scan. Genuine exhausted failures still fail the job and retain the last published board with its original timestamps. Official final-stat grading and publication remain independent of odds scanning. A successful manual run only covers its own quarter-hour slot, so it cannot suppress the next scheduled update.
