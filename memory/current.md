# Current Memory (Working State)

## Active Priorities
- Travel planner web app — implementation phase beginning across api, ui, chat, ops
- Open GitHub issues from `sync/issues/github-issues/` (requires gh CLI or web UI)
- Publish ai-meta wiki from `sync/issues/wiki/ai-meta-home.md`

## Known Issues / Risks
- gh CLI not installed — GitHub issues and wiki must be published via web UI or after `brew install gh`
- Claude API key must be provisioned in AWS Secrets Manager before chat service can function
- Mapbox API key needed for map view in ui (manage via ops Secrets Manager)

## Latest Compactions
- (updated automatically by memory_compact.sh)

## References
- Repo rules: AGENTS.md + agents/rules/
- Agent profiles: agents/profiles/
- Sync notes: sync/issues/
