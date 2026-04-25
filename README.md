# DualRead-web

Next.js Landing page + Admin console for the DualRead Chrome extension.
Public, deployed on Vercel. Phase 5 starts at Week 10 — see
[ADR-A20](../DualRead/docs/v3-1-architecture.md).

## Repo layout (3-repo split)

- `Foxsunshine/DualRead` (public) — Chrome MV3 extension
- `Foxsunshine/DualRead-web` (this repo, public) — Landing + Admin
- `Foxsunshine/DualRead-backend` (private) — FastAPI + LangGraph + eval

## Status

Phase 0 — repo scaffolded, secret defense in place. The Next.js
project is intentionally **not yet initialized**; that's a Phase 5
task so we don't carry framework deps for ten weeks before they're
exercised. When Phase 5 starts:

```sh
npx create-next-app@latest .
# adopt the existing .gitignore, .pre-commit-config.yaml, env.example
brew install pre-commit gitleaks
pre-commit install
```

## Why split the web off?

Three reasons (per ADR-A20):

1. **Independent deploy cadence** — landing page changes shouldn't
   trigger a Chrome Web Store re-review.
2. **Public source, public CI** — landing + admin can live entirely in
   the open without exposing prompt templates or rate limiters.
3. **Resume narrative** — the public TS / Next stack reads as
   recruiter-friendly evidence; the private backend reads as
   "this person ships systems that protect IP."
