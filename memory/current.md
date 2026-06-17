# Current Memory (Working State)

## Active Priorities
- Monitor PR auto-merge for api and chat (ops PRs pending CI)
- Submodule pointer bumps after all PRs merge (task #26)
- Wikis published for all four repos (tasks #11, #14, #20, #24)

## Known Issues / Risks
- CLAUDE_API_KEY must be provisioned in AWS Secrets Manager before chat service can function
- JWT auth for trips requires a token issuer (not yet implemented — trips pages fall back gracefully)
- Database-backed mode requires DATABASE_URL; mock/stub fallbacks active without it

## Latest Compactions
- (updated automatically by memory_compact.sh)

## References
- Repo rules: AGENTS.md + agents/rules/
- Agent profiles: agents/profiles/
- Sync notes: sync/issues/
