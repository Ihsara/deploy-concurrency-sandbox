# deploy-concurrency-sandbox

Throwaway experiment: what happens when several merges race through a
dev -> test -> prod pipeline with an approval gate on prod.

- `live/<env>` branches stand in for the warehouse (last deploy wins).
- `env-state/<env>` branches hold the state the next deploy diffs against.
- Repository variable `FIX` = `off` (no safeguards) or `on` (per-environment
  concurrency, refuse outdated deploys, retry the state push).
