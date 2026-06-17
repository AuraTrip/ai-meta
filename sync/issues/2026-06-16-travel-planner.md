# Sync Note: 2026-06-16 — AuraTrip Travel Planner Kickoff

## Summary
- Initiated AuraTrip travel planner web app project spanning four repos: api, ui, chat, ops.
- Defined five user-facing features: destination search, AI chat agent, itinerary generation, saved trips, map view.
- Created GitHub issue scaffolds and wiki content ready to publish once gh CLI or web UI is available.

## Scope (Repos)

- **AuraTrip/api**: Backend REST API — destination search, itinerary gen, trips CRUD, geo/map endpoints. Stack: Node.js/TypeScript, Express/Fastify, PostgreSQL.
- **AuraTrip/chat**: AI travel agent — Claude-powered multi-turn chat, intent extraction, itinerary generation via tool_use.
- **AuraTrip/ui**: Next.js frontend — search UI, chat panel, itinerary view, saved trips page, interactive map (Mapbox/Leaflet).
- **AuraTrip/ops**: Infrastructure — Terraform modules, Kubernetes manifests, GitHub Actions CI/CD pipelines.
- **AuraTrip/ai-meta**: Umbrella orchestration — this sync note, memory entry, umbrella GitHub issue, wiki overview.

## PRs / Links
- All repos: no PRs yet — implementation has not started.

## External Tracker Links
- GitHub umbrella issue: [AuraTrip/ai-meta#1](https://github.com/AuraTrip/ai-meta/issues/1)
- api sub-issue: [AuraTrip/api#1](https://github.com/AuraTrip/api/issues/1)
- chat sub-issue: [AuraTrip/chat#1](https://github.com/AuraTrip/chat/issues/1)
- ui sub-issue: [AuraTrip/ui#1](https://github.com/AuraTrip/ui/issues/1)
- ops sub-issue: [AuraTrip/ops#1](https://github.com/AuraTrip/ops/issues/1)

## Documentation Memory Links
- ai-meta wiki: https://github.com/AuraTrip/ai-meta/wiki (published)
- api wiki: https://github.com/AuraTrip/api/wiki (to be created after implementation)
- chat wiki: https://github.com/AuraTrip/chat/wiki (to be created after implementation)
- ui wiki: https://github.com/AuraTrip/ui/wiki (to be created after implementation)
- ops wiki: https://github.com/AuraTrip/ops/wiki (to be created after implementation)

## Resulting SHAs / Tags
- All repos: at HEAD of main — no changes landed yet.

## Compatibility / Notes
- Backward compatible: yes (greenfield, no existing users)
- Migration required: no
- Config/DSL impact: none
- Known risks:
  - Claude API key must be provisioned and stored in AWS Secrets Manager before chat service can function.
  - Map library (Mapbox) requires API key — coordinate with ops for secret management.
  - PostgreSQL schema migrations needed in api before trips/destinations features work.

## Follow-ups
- [x] Open umbrella issue — [AuraTrip/ai-meta#1](https://github.com/AuraTrip/ai-meta/issues/1)
- [x] Open per-repo sub-issues and link in umbrella
- [x] Publish ai-meta wiki home page — https://github.com/AuraTrip/ai-meta/wiki
- [ ] Begin implementation in api repo (destination search first — unblocks ui and chat)
- [ ] Provision Claude API key and add to Secrets Manager (ops task)
- [ ] Update this sync note with issue numbers and wiki URLs once published

## Memory Entries
- memory/inbox/2026/06/2026-06-16-travel-planner-kickoff.md (to be created)

## Verification
- Tests run: n/a (planning phase)
- Environments verified: n/a
- Observability notes: none yet
