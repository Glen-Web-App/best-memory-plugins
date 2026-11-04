# Contributing to Best Memory Plugins

Pull requests that add a plugin, fix a fact or flag a dead project are welcome. One plugin per pull request.

## Inclusion rules

An entry must:

1. **Be maintained.** At least one commit or release in the last 6 months. Archived, retired or stale plugins go to "Deprecated or not recommended", not the ranking.
2. **Ship a memory plugin for a coding agent.** A plugin, extension, hook set or documented rules pattern that installs into Claude Code, Codex, Cursor, Cline, OpenCode or another coding agent and gives it memory across sessions. A plain MCP server belongs in [Best Agent Memory MCP](https://github.com/Glen-Web-App/best-agent-memory-mcp). An agent's own built-in memory goes in the unranked "Built-in agent memory" table.
3. **Have a source for every fact.** Link the README, docs page, pricing page or release for each claim: supported agents, install command, capture model, storage, privacy defaults, pricing, license, benchmarks. A fact without a link will be removed.

## How to write an entry

- Lead with the one fact that sets the plugin apart, not its name.
- Say how capture works (hooks on which events, or a tool the agent calls) and when recall happens (every prompt, session start, on demand).
- State any default that sends prompts or code to a hosted service.
- Mark every benchmark or token-savings figure **(self-reported)** unless an independent party ran it, and link the run.
- List real weaknesses. An entry with no weaknesses will not be merged.
- No marketing language and no em dashes.

## Ranking changes

Rank moves follow the criteria in the README's "How we ranked" section. Explain in the pull request which criterion changed. First place is the maintainer's pick and is disclosed as such in the README.

## Corrections from maintainers

If you maintain a listed plugin and something is wrong or out of date, open an issue or pull request with a link to the current source.
