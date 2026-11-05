<div align="center">

# Best Memory Plugins

**The best memory plugins for AI coding agents, ranked: persistent memory for Claude Code, Codex, Cursor, OpenCode, Cline and more.**

[![List](https://img.shields.io/badge/list-curated-fc60a8?style=flat-square&logo=awesomelists&logoColor=white)](#the-ranked-list)
[![Last updated](https://img.shields.io/badge/updated-November%202026-blue?style=flat-square)](#how-we-ranked)
[![Entries](https://img.shields.io/badge/entries-24-informational?style=flat-square)](#at-a-glance)
[![License: CC0-1.0](https://img.shields.io/badge/license-CC0--1.0-lightgrey?style=flat-square)](LICENSE)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](CONTRIBUTING.md)

</div>

Best Memory Plugins ranks 24 plugins and extensions that give a coding agent persistent memory between sessions: what it decided, what failed, what the codebase looks like. If you are looking for a Claude Code memory plugin, this list puts claude-mem, Supermemory, Hindsight, Mem0 and 19 others side by side, along with how each one captures memory (hooks on every turn, or a tool the agent has to remember to call), where it stores it, and whether it also covers Codex, Cursor and other agents. The memory each agent ships on its own (Claude Code auto memory, Codex memories, Copilot Memory and others) is compared separately, because it is what every plugin here builds on or replaces.

**Short answer.** For a team that wants one memory across everyone's agents, Glen. For a solo Claude Code user who wants automatic local capture, claude-mem (switch its observer to local). For hook-driven recall on every prompt across four agents, Supermemory. For no LLM and no cloud at all, deja-vu or projectmem.

> **Disclosure:** this list is maintained by the Glen team, and Glen is ranked first. Every other entry is ranked on the [published criteria](#how-we-ranked), and its facts link to their sources.

## Contents

- [At a glance](#at-a-glance)
- [How we ranked](#how-we-ranked)
- [The ranked list](#the-ranked-list)
- [Built-in agent memory (not ranked)](#built-in-agent-memory-not-ranked)
- [Deprecated or not recommended](#deprecated-or-not-recommended)
- [FAQ](#faq)
- [Related](#related)
- [Contributing](#contributing)
- [License](#license)

## At a glance

Star badges are live. Where a plugin lives inside a larger monorepo, the badge counts the whole repo; the entry says so.

| # | Plugin | Hosted or local | Memory stored as | Capture | Team sharing | License | Stars |
|---|---|---|---|---|---|---|---|
| 1 | [Glen](https://tryglen.com) | Hosted | Shards and observations on Glen's servers | Hooks every turn; recall every prompt (on demand in Cursor, Grok) | Org-wide, access checked per observation | Plugin MIT; hosted service | [site](https://tryglen.com) |
| 2 | [claude-mem](https://github.com/thedotmack/claude-mem) | Local; hosted observer by default | SQLite FTS5 + Chroma | Six lifecycle hooks | Opt-in TeamBrain | Apache-2.0 | ![](https://img.shields.io/github/stars/thedotmack/claude-mem?style=flat-square&label=) |
| 3 | [Supermemory](https://github.com/supermemoryai/claude-supermemory) | Hosted; self-host option | Supermemory cloud container | Hooks; search on every prompt | Team-named namespace | MIT (README badge) | ![](https://img.shields.io/github/stars/supermemoryai/claude-supermemory?style=flat-square&label=) |
| 4 | [Hindsight](https://github.com/vectorize-io/hindsight) | Cloud default; self-host or local daemon | Per-repo bank (Postgres + pgvector) | Hooks; synthesis on first prompt | One bank for all agents; Cloud teams | MIT | ![](https://img.shields.io/github/stars/vectorize-io/hindsight?style=flat-square&label=) |
| 5 | [agentmemory](https://github.com/rohitg00/agentmemory) | Local | Local data dir, BM25 + optional embeddings | Hooks (12 in Claude Code) | One server for your agents | Apache-2.0 | ![](https://img.shields.io/github/stars/rohitg00/agentmemory?style=flat-square&label=) |
| 6 | [Mem0 plugin](https://github.com/mem0ai/mem0/tree/main/integrations/claude-code-plugin) | Hosted | Mem0 Platform + local queue | Hooks; recall on first prompt | Shared project pool | Apache-2.0 | ![](https://img.shields.io/github/stars/mem0ai/mem0?style=flat-square&label=) |
| 7 | [Cognee memory](https://github.com/topoteretes/cognee-integrations) | Local default; Cognee Cloud | Cognee graph + vector | Hooks; inject on prompt submit | Not documented | Apache-2.0 | ![](https://img.shields.io/github/stars/topoteretes/cognee-integrations?style=flat-square&label=) |
| 8 | [Claude Subconscious](https://github.com/letta-ai/claude-subconscious) | Letta Cloud or self-hosted Letta | Letta agent memory | Async hooks feed a background agent | Not documented | MIT | ![](https://img.shields.io/github/stars/letta-ai/claude-subconscious?style=flat-square&label=) |
| 9 | [mcp-memory-service](https://github.com/doobidoo/mcp-memory-service) | Local or self-hosted | SQLite + local ONNX embeddings | Hooks (Claude Code, Codex) | Self-hosted HTTP sync | Apache-2.0 | ![](https://img.shields.io/github/stars/doobidoo/mcp-memory-service?style=flat-square&label=) |
| 10 | [deja-vu](https://github.com/vshulcz/deja-vu) | Local | Index of transcripts already on disk | Hooks; no LLM calls | None described | MIT | ![](https://img.shields.io/github/stars/vshulcz/deja-vu?style=flat-square&label=) |
| 11 | [MemPalace](https://github.com/MemPalace/mempalace) | Local; team server option | Verbatim text | Auto-save hooks + transcript mining | Team server compose file | MIT | ![](https://img.shields.io/github/stars/MemPalace/mempalace?style=flat-square&label=) |
| 12 | [Episodic Memory](https://github.com/obra/episodic-memory) | Local | SQLite + sqlite-vec | Hooks archive transcripts; search on demand | None described | MIT | ![](https://img.shields.io/github/stars/obra/episodic-memory?style=flat-square&label=) |
| 13 | [memsearch](https://github.com/zilliztech/memsearch) | Local | Daily Markdown files + Milvus index | Every turn captured; recall by skill | Not documented | MIT | ![](https://img.shields.io/github/stars/zilliztech/memsearch?style=flat-square&label=) |
| 14 | [Basic Memory](https://github.com/basicmachines-co/basic-memory) | Local; paid cloud | Markdown files + SQLite index | Agent writes notes; briefing hooks | Basic Memory Teams (paid) | AGPL-3.0 | ![](https://img.shields.io/github/stars/basicmachines-co/basic-memory?style=flat-square&label=) |
| 15 | [Engram](https://github.com/Gentleman-Programming/engram) | Local | SQLite + FTS5 | Tool calls; plugins | Git Sync | MIT | ![](https://img.shields.io/github/stars/Gentleman-Programming/engram?style=flat-square&label=) |
| 16 | [Beads](https://github.com/gastownhall/beads) | Local; Dolt remotes | Dolt version-controlled SQL | `bd remember`, injected by `bd prime` | Dolt remotes | MIT | ![](https://img.shields.io/github/stars/gastownhall/beads?style=flat-square&label=) |
| 17 | [projectmem](https://github.com/riponcm/projectmem) | Local, in the repo | `.projectmem/` files | Git hooks + file watcher | Distilled files committed to git | MIT | ![](https://img.shields.io/github/stars/riponcm/projectmem?style=flat-square&label=) |
| 18 | [LongMemory](https://github.com/CaviraOSS/LongMemory) | Local | SQLite + embeddings | Session porter imports logs; plugins | Not documented | Apache-2.0 | ![](https://img.shields.io/github/stars/CaviraOSS/LongMemory?style=flat-square&label=) |
| 19 | [Nowledge Mem](https://github.com/nowledge-co/community) | Nowledge Mem app | Not documented | Hooks | Not documented | No license file | ![](https://img.shields.io/github/stars/nowledge-co/community?style=flat-square&label=) |
| 20 | [memU](https://github.com/NevaMind-AI/memU) | Local or memU Cloud | Writes into `CLAUDE.md` / `AGENTS.md` | Adapters read session JSONL | Not documented | Not detected | ![](https://img.shields.io/github/stars/NevaMind-AI/memU?style=flat-square&label=) |
| 21 | [Zep Context plugin](https://github.com/getzep/zep-context-plugin) | Hosted | Temporal knowledge graph | Tool calls guided by a skill | Shared Context Graphs | Plugin Apache-2.0; cloud proprietary | ![](https://img.shields.io/github/stars/getzep/zep-context-plugin?style=flat-square&label=) |
| 22 | [Serena](https://github.com/oraios/serena) | Local | Not documented | Agent calls a tool | Not documented | GPL-3.0-or-later (app) | ![](https://img.shields.io/github/stars/oraios/serena?style=flat-square&label=) |
| 23 | [Pieces](https://pieces.app) | Local (desktop app) | PiecesOS on-device store | OS-level capture; recall over MCP | Enterprise plan | Proprietary | closed source |
| 24 | [Cline Memory Bank](https://docs.cline.bot/prompting/cline-memory-bank) | Local, in the repo | Six Markdown files in `memory-bank/` | You ask Cline to update | Through git | Docs pattern | ![](https://img.shields.io/github/stars/nickbaumann98/cline_docs?style=flat-square&label=) |

## How we ranked

Glen's first place is the maintainer's pick. Entries 2 to 24 are ordered on these criteria, read from each project's README, docs, pricing page and the GitHub API in early November 2026:

1. **Maintained.** A commit or release in the last 6 months. Archived, retired and stale plugins go to [Deprecated or not recommended](#deprecated-or-not-recommended).
2. **Ships a memory plugin for a coding agent.** A plugin, extension, hook set or documented rules pattern that installs into the agent. Projects that reach coding agents only through a generic MCP connection (MemOS, Memori) or index code rather than conversations (`DeusData/codebase-memory-mcp`, `zilliztech/claude-context`) are left out. The [Best Agent Memory MCP](https://github.com/Glen-Web-App/best-agent-memory-mcp) list covers MCP-only servers.
3. **Capture model.** Hooks that capture every turn and inject on every prompt rank above hooks that inject only at session start, which rank above a store the agent has to remember to call.
4. **Retrieval quality evidence.** Benchmarks and token or cost savings in this category are vendor-reported, so they are labeled **(self-reported)** and weigh little. Disputed results are flagged.
5. **Setup effort.** One install command beats a stack of background services, API keys and manual hook setup.
6. **Team sharing.** A documented way for teammates' agents to read the same memory ranks above per-machine storage.
7. **Licensing and pricing transparency.** A license file and a public price list rank above neither. A default that quietly sends prompts to a hosted service counts against an entry.

Monorepo stars overstate how many people use a plugin. Supermemory's core repo has 31,522 stars, its Claude Code plugin 2,798; Cognee's core has 33,043, its integrations repo 104 (all as of 2026-11-03).

## The ranked list

### 🥇 1. Glen

[![Website](https://img.shields.io/badge/site-tryglen.com-111111?style=flat-square)](https://tryglen.com)
![License](https://img.shields.io/badge/plugin-MIT-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/Glen-Web-App/glen-claude-code-plugin?style=flat-square)

Hooks on SessionStart, UserPromptSubmit and Stop call the glen CLI, so every turn is recorded and relevant team context is injected on every prompt, from one org memory that every teammate's agent reads and writes. Access control runs per observation at recall, so an agent only gets what its user is already cleared to see.

| | |
|---|---|
| Agents | Claude Code, Codex, Cursor, Grok Build CLI, jcode, pi; any MCP client for search |
| Capture | Automatic on every turn through the hooks |
| Recall | Injected on every prompt in Claude Code, Codex and pi; on demand through `glen search` in Cursor and Grok |
| Storage | Shards and observations on Glen's servers; LLM relevance passes pick what to inject |
| Other sources | Slack public channels, GitHub, tickets, docs, and calls through Fireflies, Fathom and Granola |
| Pricing | Free plan to start; paid plans exist; no public pricing page |

One command detects installed agents and sets up each plugin and its hooks:

```bash
npx @tryglen/cli@latest install
```

Or install the Claude Code plugin by hand:

```bash
claude plugin marketplace add Glen-Web-App/glen-claude-code-plugin
claude plugin install glen@glen
```

The plugin ships skills for search, code-search, forget, controls, setup, create-skill and use-skill, create-artifact and use-artifact, import-transcripts, invite, feedback and session-takeover. `glen import` back-fills old local agent sessions, so memory starts with history. `glen code-search` traces lines of code to the agent conversations that wrote them, `glen takeover <code>` picks up a teammate's session, and `glen review` runs a local PR reviewer. For privacy, `glen off` stops everything, `glen incognito` keeps recall but records nothing, and `glen silent` records but injects nothing; a macOS menu-bar indicator shows when recording is on.

**Strengths**
- Shared by default: one org memory for every teammate's agents, with access checked per observation at recall.
- Recall is injected on every prompt by a hook (Claude Code, Codex, pi), not left to the model to request.
- Contradiction detection: when a newer decision contradicts an older one, the older one stops being recalled.
- A shared skills library: team skills are offered to agents automatically.
- Benchmark on tryglen.com: 21% faster to a merged change and 29% fewer tokens per task (self-reported).

**Weaknesses**
- Cloud service: memory lives on Glen's servers, not in local files.
- Requires a Glen account and an org.
- Cursor and Grok get on-demand recall only (`glen search`), not per-prompt injection.
- The most value comes with a team; a solo developer gets less from shared memory.
- Connecting only the MCP server does not record; recording needs the plugin hooks.

**Best for:** teams who want every teammate's coding agent to start from what the rest of the team already decided.

### 🥈 2. claude-mem

[![Stars](https://img.shields.io/github/stars/thedotmack/claude-mem?style=flat-square&label=stars)](https://github.com/thedotmack/claude-mem)
![License](https://img.shields.io/badge/license-Apache--2.0-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/thedotmack/claude-mem?style=flat-square)

112,227 stars as of 2026-11-03, by far the most of any dedicated coding-agent memory plugin. Six lifecycle hooks (SessionStart, UserPromptSubmit, PreToolUse, PostToolUse, Stop, SessionEnd) record tool-use observations, and AI-compressed summaries appear in new sessions automatically ([README](https://github.com/thedotmack/claude-mem)).

**Key facts:** Claude Code, OpenCode 1.3.4+, T3 Code (Codex and Claude Code providers), Antigravity CLI, Oh My Pi, Pi, DeepSeek Harness, Grok Bot, OpenClaw; docs also list Cursor, Windsurf and Codex CLI · local SQLite (FTS5) + Chroma in `~/.claude-mem/`, with a Bun worker and web viewer · optional Cloud Sync to cmem.ai and an opt-in TeamBrain workspace where "Each person chooses what to share" · CMEM Pro price not published.

```bash
npx claude-mem install
# or, in Claude Code
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem
```

**Strengths**
- Capture needs no manual calls.
- One installer covers the broadest harness list in this ranking.
- `<private>` tags keep content out of storage, and screenshots are off by default.

**Weaknesses**
- The installer defaults to the hosted CMEM Pro observer (30-day free trial, no card), which runs inference through the cmem.ai gateway, so prompts leave the machine. Opt out with `--provider host` or `CLAUDE_MEM_ONLINE_OPTIN=false` ([docs](https://docs.claude-mem.ai/installation)).
- A heavy stack: Node 20+, Bun, uv, SQLite, Chroma and a background worker.
- One user's analysis measured about 42,000 cache-creation tokens per session (single user, v9.x, December 2025) ([write-up](https://glama.ai/mcp/servers/@Vvkmnn/claude-historian/blob/5523c7a4febebd9cb3e54990eb6bc693ee206aa5/COMPARISON.md)).
- `npm install -g claude-mem` installs only the SDK, and a marketplace-only install builds the hook launcher during the first session, which can run without memory. 125 open issues.

**Best for:** solo Claude Code users who want automatic capture and are willing to set the observer to local.

### 🥉 3. Supermemory

[![Stars](https://img.shields.io/github/stars/supermemoryai/claude-supermemory?style=flat-square&label=stars)](https://github.com/supermemoryai/claude-supermemory)
![License](https://img.shields.io/badge/license-MIT%20(README)-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/supermemoryai/claude-supermemory?style=flat-square)

The UserPromptSubmit hook runs the search itself and injects fresh matches, so recall does not depend on the model choosing to call a tool ([README](https://github.com/supermemoryai/claude-supermemory)).

**Key facts:** plugins for Claude Code, OpenCode, Codex and Cursor, which write to one shared repo container (`sm_scope: personal`), with a `namespace` override for a team-named container · four hooks: SessionStart loads profile facts, UserPromptSubmit searches, PreToolUse, and Stop saves the conversation delta in the background · Supermemory cloud by default, self-host with `npx supermemory local` · Free $0 ($5 credits, 1 seat), Pro $19/mo (3 seats), Max $100/mo, Scale $399/mo; the pricing page says all plans include all plugins ([pricing](https://supermemory.ai/pricing)).

```bash
/plugin install supermemory@supermemory-plugins
```

**Strengths**
- The same memory follows you across four agents.
- A `context-gatherer` subagent and `/supermemory:index` for indexing the codebase.
- Redacts credential-shaped values (provider tokens, private keys, Bearer tokens, URL credentials); OpenCode skips anything in `<private>` tags.

**Weaknesses**
- Cloud by default, billed in usage credits.
- No license set in the GitHub API for the plugin repos (the README badge says MIT), and the README admits redaction "cannot detect every secret".
- The old `claude-supermemory` plugin must be uninstalled first, and `claude plugin validate` rejects one hook event on Claude Code 2.1.250.
- The Cursor and Codex plugins are young (35 and 58 stars as of 2026-11-03).

**Best for:** developers who switch between Claude Code, Codex, Cursor and OpenCode and want recall on every prompt.

### 4. Hindsight

[![Stars](https://img.shields.io/github/stars/vectorize-io/hindsight?style=flat-square&label=stars)](https://github.com/vectorize-io/hindsight)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/vectorize-io/hindsight?style=flat-square)

One installer covers 13 agents, and before the first prompt it builds a per-repo memory bank from git history and past sessions ([coding agents docs](https://hindsight.vectorize.io/sdks/integrations/coding-agents)).

**Key facts:** Claude Code, Codex CLI, Cursor CLI, Copilot CLI, opencode, Kilo CLI, Cline CLI, Antigravity CLI, Devin CLI, pi, Prime Agent, Grok Build, DeepSeek Harness · bank `coding-agent::{gitProject}` shared by all agents · cloud (default), self-hosted, or a local daemon at `127.0.0.1:9077` · Hindsight Cloud is usage-based with free credits; self-hosting is free under MIT · the codebase survey has a default $2 spend cap.

```bash
npx @vectorize-io/hindsight-coding-agents install all
```

**Strengths**
- Session start seeds the bank and runs a codebase survey; Stop writes the transcript back.
- Privacy switches: `disabled`, `optInOnly` with `optInPaths`, `retainSessions: false`, and an opt-in Memory Defense that redacts or blocks 45 secret and PII patterns.
- Vendor benchmark: Claude Code cost per task fell from $0.445 to $0.338 with memory (self-reported).

**Weaknesses**
- Plugin churn: the original `hindsight-memory` Claude Code plugin is no longer maintained, and its settings do not carry over.
- Cloud mode is the default.
- Recall is a synthesis on the first prompt by default, not on every prompt.

**Best for:** developers who use many coding agents on the same repo and want them to share one memory bank.

### 5. agentmemory

[![Stars](https://img.shields.io/github/stars/rohitg00/agentmemory?style=flat-square&label=stars)](https://github.com/rohitg00/agentmemory)
![License](https://img.shields.io/badge/license-Apache--2.0-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/rohitg00/agentmemory?style=flat-square)

Native plugins with hooks for three agents (12 hooks in Claude Code, 6 in Codex CLI, lifecycle hooks in Cursor) and an MCP server for the rest, all pointing at one local server that works without an API key ([README](https://github.com/rohitg00/agentmemory)).

**Key facts:** also Copilot CLI, Gemini CLI, OpenCode, Hermes, OpenClaw, pi, Oh My Pi, DeepSeek Harness · local data directory, server on `localhost:3111` and viewer on `:3113`, both on loopback · recall with `memory_recall` (BM25) or `memory_smart_search`; embeddings optional.

```bash
npx -y @agentmemory/agentmemory@latest
# then, in Claude Code
/plugin marketplace add rohitg00/agentmemory
```

**Strengths**
- Hooks record prompts, tool events and final replies with no manual calls.
- API keys, secrets and `<private>` content are stripped before storage.
- Keyless mode means nothing leaves the machine.

**Weaknesses**
- Benchmarks are self-published.
- 528 open issues for a repo created 2026-02-25.

**Best for:** a single developer running several agents locally who wants hooks without a cloud account.

### 6. Mem0 plugin

[![Stars](https://img.shields.io/github/stars/mem0ai/mem0?style=flat-square&label=monorepo%20stars)](https://github.com/mem0ai/mem0)
![License](https://img.shields.io/badge/license-Apache--2.0-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/mem0ai/mem0?style=flat-square)

Splits memory into a shared project pool ("Everyone on the repo reads and writes the same pool") and personal memory that stays private to you ([plugin README](https://github.com/mem0ai/mem0/tree/main/integrations/claude-code-plugin)).

**Key facts:** official Mem0 plugin v0.3.3; the monorepo also ships Codex, Cursor, OpenCode, Antigravity, DeepSeek, Kimi, Pi, Hermes and OpenClaw plugins · hooks capture prompts, answers, changed file paths and test or build results locally with no model call; every 5 exchanges a background worker flushes to Mem0 · recall on the next session's first prompt (20+ characters) returns up to 5 memories · `/mem0:search`, `/mem0:status`, a read-only `search_memories` tool · needs a Mem0 Platform API key · the star badge is the whole mem0 monorepo.

```bash
claude plugin marketplace add mem0ai/mem0
claude plugin install mem0@mem0-plugins --scope user --config api_key="$MEM0_API_KEY"
```

**Strengths**
- Team sharing is built into the plugin.
- Capture never calls a model, and writes are batched.
- Ships a Sonnet "sidekick" subagent that works in a separate worktree.

**Weaknesses**
- A cloud API key is mandatory; no local mode is documented for the plugin.
- Recall happens only on the session's first prompt by default.
- Usage telemetry "is not anonymous" (sent under your Mem0 account email), though it excludes prompts, memory text, paths, repo names and keys.
- A recent breaking update: "Memories carry over, most local config does not."

**Best for:** a team on Mem0 Platform that wants a shared project memory in Claude Code.

### 7. Cognee memory plugin

[![Stars](https://img.shields.io/github/stars/topoteretes/cognee-integrations?style=flat-square&label=stars)](https://github.com/topoteretes/cognee-integrations)
![License](https://img.shields.io/badge/license-Apache--2.0-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/topoteretes/cognee-integrations?style=flat-square)

Local by default: the plugin starts a Cognee API on `localhost:8011` and extracts memory with your own LLM key, or points at Cognee Cloud with `COGNEE_BASE_URL` and `COGNEE_API_KEY` ([README](https://github.com/topoteretes/cognee-integrations)).

**Key facts:** Claude Code plugin plus a Codex plugin marketplace in the same repo · captures prompts, tool traces and assistant responses, and injects relevant context on prompt submit · `remember` tool · credential and key files are never captured; `COGNEE_CAPTURE=false` turns capture off.

```bash
/plugin marketplace add topoteretes/cognee-integrations
/plugin install cognee-memory@cognee
```

**Strengths**
- Recall injected on prompt submit.
- Runs fully local if you bring an LLM key.

**Weaknesses**
- Local mode needs Python 3.10 to 3.14 and an LLM key for extraction.
- A small integration repo (104 stars, 57 open issues as of 2026-11-03); the 33,043 stars belong to Cognee core.

**Best for:** Claude Code or Codex users who want graph-backed memory on their own machine.

### 8. Claude Subconscious

[![Stars](https://img.shields.io/github/stars/letta-ai/claude-subconscious?style=flat-square&label=stars)](https://github.com/letta-ai/claude-subconscious)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/letta-ai/claude-subconscious?style=flat-square)

After each response, an async hook sends the transcript to a background Letta agent that can read files, search the web and update its memory, then "whispers back" through hooks ([README](https://github.com/letta-ai/claude-subconscious)).

**Key facts:** Claude Code only · hooks on SessionStart, UserPromptSubmit (injects memory through stdout) and PreToolUse (mid-workflow updates) · needs `LETTA_API_KEY` from app.letta.com, or `LETTA_BASE_URL` for self-hosted Letta · default agent model `zai/glm-5`, described as free on Letta Cloud · never writes `CLAUDE.md`.

```bash
/plugin install claude-subconscious@claude-subconscious
```

**Strengths**
- The memory keeper is an agent that can read files and search the web, rather than a passive store.
- `LETTA_MODE=off` and `LETTA_SDK_TOOLS` (read-only by default, or full, or off) control what it can do.

**Weaknesses**
- Every transcript goes to Letta, which is the cloud unless you self-host.
- In `full` mode the background agent can run Bash, Edit and Write.
- Claude Code only.

**Best for:** Claude Code users who want a second agent maintaining memory in the background.

### 9. mcp-memory-service

[![Stars](https://img.shields.io/github/stars/doobidoo/mcp-memory-service?style=flat-square&label=stars)](https://github.com/doobidoo/mcp-memory-service)
![License](https://img.shields.io/badge/license-Apache--2.0-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/doobidoo/mcp-memory-service?style=flat-square)

Configurable Claude Code hooks capture sessions automatically, and `python3 codex/install_hooks.py` installs the same for Codex, all on a memory server you host ([README](https://github.com/doobidoo/mcp-memory-service)).

**Key facts:** MCP plus REST memory backend · SQLite, Cloudflare, Hybrid (local reads with cloud sync) or Milvus · local ONNX embeddings, no API key · self-hosted team sync over HTTP · v12.5.0 released 2026-11-03.

```bash
pip install mcp-memory-service
python3 codex/install_hooks.py
```

**Strengths**
- Team sharing without a vendor cloud.
- Embeddings run locally.

**Weaknesses**
- Hooks exist for Claude Code and Codex; other agents connect through MCP tools only.
- Many backends to choose from, and cloud sync depends on Cloudflare.

**Best for:** a team that wants hook-based capture on a server it controls.

### 10. deja-vu

[![Stars](https://img.shields.io/github/stars/vshulcz/deja-vu?style=flat-square&label=stars)](https://github.com/vshulcz/deja-vu)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/vshulcz/deja-vu?style=flat-square)

"Zero LLM calls, no cloud account": one Go binary indexes the transcripts that 43 agents already keep on disk and offers prior sessions back through hooks ([README](https://github.com/vshulcz/deja-vu)).

**Key facts:** recall at session start, before a file edit or command, and when a command fails · credentials redacted at index time as `[redacted:<kind>]` · also a Claude Code marketplace plugin · created 2026-07-14.

```bash
deja install --auto
```

**Strengths**
- Useful immediately on existing history.
- Nothing leaves the machine.

**Weaknesses**
- Recalls raw transcripts, not curated facts.
- Young project, per machine only.

**Best for:** zero-config local recall across every agent on one laptop.

### 11. MemPalace

[![Stars](https://img.shields.io/github/stars/MemPalace/mempalace?style=flat-square&label=stars)](https://github.com/MemPalace/mempalace)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/MemPalace/mempalace?style=flat-square)

Auto-save hooks for Claude Code, Codex CLI and Cursor IDE (Cursor also gets session-start recall), over local verbatim storage that makes zero API calls ([README](https://github.com/MemPalace/mempalace)).

**Key facts:** `mempalace mine` imports existing transcripts · pluggable backends including local SQLite and pgvector · optional team server through docker-compose · LongMemEval 96.6% R@5 (self-reported, disputed).

```bash
pip install mempalace
mempalace mine ~/.claude/projects/ --mode convos
```

**Strengths**
- No API key in raw mode.
- `mempalace mine` imports the Claude Code transcripts already on disk.

**Weaknesses**
- Hooks are a separate setup step, and the README warns that Claude Code sessions expire in 30 days without them.
- The benchmark figure is retrieval recall shown next to other systems' QA accuracy; an [arXiv paper](https://arxiv.org/pdf/2604.21284) and press coverage dispute the framing.
- 823 open issues as of 2026-11-03.

**Best for:** keeping a verbatim, searchable archive of agent conversations on your own machine.

### 12. Episodic Memory

[![Stars](https://img.shields.io/github/stars/obra/episodic-memory?style=flat-square&label=stars)](https://github.com/obra/episodic-memory)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/obra/episodic-memory?style=flat-square)

Searches full past conversations from five agents (Claude Code, Codex 0.130.0+, Cursor, opencode, Oh My Pi), summarized with your existing Claude Code auth and indexed locally ([README](https://github.com/obra/episodic-memory)).

**Key facts:** part of the Superpowers marketplace · session sync copies transcripts to an archive, summarizes them (Haiku by default) and indexes them in SQLite with sqlite-vec · recall through MCP search and read tools and a skill.

```bash
/plugin install episodic-memory@superpowers-marketplace
```

**Strengths**
- Full-conversation search across five agents.
- Local search, no cloud.
- Can back-fill older Cursor history.

**Weaknesses**
- No automatic injection; the agent has to search.
- Summarization spends your Claude or Codex usage, and Codex needs `codex features enable plugin_hooks` plus trusting the hook.
- 500 stars and 42 open issues, last push 2026-09-10; the Superpowers framework's much larger star count does not apply to this plugin.

**Best for:** finding "how did we solve this last time" across agents, on demand.

### 13. memsearch

[![Stars](https://img.shields.io/github/stars/zilliztech/memsearch?style=flat-square&label=stars)](https://github.com/zilliztech/memsearch)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/zilliztech/memsearch?style=flat-square)

The Markdown files are the primary record: every turn lands in a daily `.memsearch/memory/YYYY-MM-DD.md` file, and Milvus is a shadow index on top ([README](https://github.com/zilliztech/memsearch)).

**Key facts:** from Zilliz · plugins for Claude Code, Codex (install script), OpenCode, OpenClaw and DeepSeek Harness · recall through the `/memory-recall` skill.

```bash
/plugin marketplace add zilliztech/memsearch
/plugin install memsearch
```

**Strengths**
- Capture of every conversation turn is automatic.
- Memory stays readable as dated Markdown files.

**Weaknesses**
- The Codex setup asks for `codex --yolo`, "needed for ONNX model network access".
- Recall in Claude Code is skill or command driven, not injected.
- 262 open issues as of 2026-11-03.

**Best for:** people who want a plain-text journal of agent sessions with vector search added.

### 14. Basic Memory

[![Stars](https://img.shields.io/github/stars/basicmachines-co/basic-memory?style=flat-square&label=stars)](https://github.com/basicmachines-co/basic-memory)
![License](https://img.shields.io/badge/license-AGPL--3.0-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/basicmachines-co/basic-memory?style=flat-square)

`--scope project` declares the Claude Code plugin in the repo's settings, so teammates pick it up from the repo; memory itself is Markdown you can open in Obsidian ([README](https://github.com/basicmachines-co/basic-memory)).

**Key facts:** Claude Code plugin with session-start briefings, pre-compaction checkpoints, an opt-in capture output style and `/basic-memory:remember`, `:share`, `:status` · also Codex, Cursor, VS Code, Claude Desktop, ChatGPT and a Hermes plugin through MCP · local SQLite index with hybrid full-text and vector search (FastEmbed) · local is free; Cloud $15/mo beta price (regular $19), 7-day trial.

```bash
uv tool install basic-memory --prerelease=allow
bm install claude-code
```

**Strengths**
- Human-readable Markdown, with no lock-in.
- Briefings and checkpoints around compaction.

**Weaknesses**
- AGPL-3.0.
- Without `--prerelease=allow` the install "silently installs an older release", and the plugin needs the MCP server connected first.
- Capture is not automatic per turn; the agent writes notes.

**Best for:** teams who want agent memory as notes they can review in a pull request.

### 15. Engram

[![Stars](https://img.shields.io/github/stars/Gentleman-Programming/engram?style=flat-square&label=stars)](https://github.com/Gentleman-Programming/engram)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/Gentleman-Programming/engram?style=flat-square)

Fourteen setup targets from one Go binary (`engram setup claude-code`, `codex`, `windsurf`, `cursor`, plus OpenCode, Gemini CLI, VS Code and more), with plugins for OpenCode and Claude Code ([README](https://github.com/Gentleman-Programming/engram)).

**Key facts:** SQLite + FTS5 at `~/.engram/engram.db` · Git Sync for sharing across machines; optional Engram Cloud · flags related or conflicting memories.

```bash
brew install gentleman-programming/tap/engram
engram setup claude-code
```

**Strengths**
- No runtime dependencies.
- Team sharing through Git.

**Weaknesses**
- The README does not spell out how much the plugins save without a tool call.
- Keyword search only, and the Codex integration has version preconditions.

**Best for:** a light, local memory shared through the repo's Git workflow.

### 16. Beads

[![Stars](https://img.shields.io/github/stars/gastownhall/beads?style=flat-square&label=stars)](https://github.com/gastownhall/beads)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/gastownhall/beads?style=flat-square)

A dependency-aware issue graph first and a memory store second: `bd remember "insight"` saves project memory and `bd prime` injects it, all in a Dolt version-controlled SQL database ([README](https://github.com/gastownhall/beads)).

**Key facts:** `bd setup claude` or `bd setup codex` installs hooks and skills · sync across machines and teammates through Dolt remotes · formerly `steveyegge/beads`.

```bash
bd setup claude
```

**Strengths**
- Tasks and memory in one versioned database.
- Team sync without a vendor cloud.

**Weaknesses**
- A task tracker first; memory is a smaller part.
- 1,610 open issues as of 2026-11-03.

**Best for:** agents that work through long task lists and need to remember what is blocked on what.

### 17. projectmem

[![Stars](https://img.shields.io/github/stars/riponcm/projectmem?style=flat-square&label=stars)](https://github.com/riponcm/projectmem)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/riponcm/projectmem?style=flat-square)

"No cloud, no telemetry, no accounts": memory lives in `.projectmem/` inside the repo, with distilled files committed and the raw log gitignored ([README](https://github.com/riponcm/projectmem)).

**Key facts:** `pjm init` installs three git hooks and a file watcher · MCP server with 17 tools for Claude Code, Claude Desktop, Cursor, Antigravity and Codex · `pjm wrap claude` injects a token-budgeted block at session start · created 2026-05-09.

```bash
pip install projectmem
pjm init
pjm wrap claude
```

**Strengths**
- Memory travels with the repo, so teammates get it through git.
- Nothing leaves the machine.

**Weaknesses**
- Young project (876 stars as of 2026-11-03).
- Session-start injection needs the `pjm wrap` launcher.

**Best for:** repos where project memory should be reviewed and committed like code.

### 18. LongMemory

[![Stars](https://img.shields.io/github/stars/CaviraOSS/LongMemory?style=flat-square&label=stars)](https://github.com/CaviraOSS/LongMemory)
![License](https://img.shields.io/badge/license-Apache--2.0-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/CaviraOSS/LongMemory?style=flat-square)

A session porter imports logs from Claude Code, Codex, OpenCode, Gemini CLI, Copilot Chat and Cline into one local SQLite store ([README](https://github.com/CaviraOSS/LongMemory)).

**Key facts:** Claude Code plugin, Codex and ChatGPT desktop plugin, VS Code extension · formerly CaviraOSS OpenMemory; the package is now `longmemory-sdk`.

```bash
longmemory port --from claude-code
```

**Strengths**
- Back-fills memory from six agents.
- Local-first.

**Weaknesses**
- The rename from OpenMemory (`pip uninstall openmemory-py && pip install longmemory-sdk`) and the unrelated Mem0 OpenMemory cause confusion.
- Scope extends well beyond memory (skills, LLM wiki, CodeGraph).

**Best for:** consolidating history from several agents into one local store.

### 19. Nowledge Mem

[![Stars](https://img.shields.io/github/stars/nowledge-co/community?style=flat-square&label=stars)](https://github.com/nowledge-co/community)
![Last commit](https://img.shields.io/github/last-commit/nowledge-co/community?style=flat-square)

One of the longest agent lists here: plugins for Claude Code, Copilot CLI, Codex, Cursor, Gemini CLI, Pi, OMP, Droid, Devin, Grok Build and more, all backed by the Nowledge Mem app and its `nmem` CLI ([README](https://github.com/nowledge-co/community)).

**Key facts:** community plugins repo plus product repo [nowledge-co/nowledge-mem](https://github.com/nowledge-co/nowledge-mem) · pricing not published in the sources we checked.

```bash
claude plugin marketplace add https://github.com/nowledge-co/community
claude plugin install nowledge-mem@nowledge-community
```

**Strengths**
- Wide agent coverage from one memory app.

**Weaknesses**
- No license on either repo.
- Requires installing the Nowledge Mem app and the `nmem` CLI first.
- 241 open issues on the community repo as of 2026-11-03.

**Best for:** Nowledge Mem users who want the same memory inside their coding agents.

### 20. memU

[![Stars](https://img.shields.io/github/stars/NevaMind-AI/memU?style=flat-square&label=stars)](https://github.com/NevaMind-AI/memU)
![Last commit](https://img.shields.io/github/last-commit/NevaMind-AI/memU?style=flat-square)

Writes memory back into the agent's own instruction files: the host adapters `memu-claude-code`, `memu-codex` and `memu-cursor` read session JSONL and update `~/.claude/CLAUDE.md` or `~/.codex/AGENTS.md` ([README](https://github.com/NevaMind-AI/memU)).

**Key facts:** Local or memU Cloud backend · GitHub does not detect a license (NOASSERTION).

**Strengths**
- Memory lands where the agent already reads it, so no extra tool or hook is needed at recall.

**Weaknesses**
- It edits your global instruction files, so review what it writes.
- License not detected by GitHub.

**Best for:** developers who want CLAUDE.md or AGENTS.md kept up to date from their sessions.

### 21. Zep Context plugin

[![Stars](https://img.shields.io/github/stars/getzep/zep-context-plugin?style=flat-square&label=stars)](https://github.com/getzep/zep-context-plugin)
![License](https://img.shields.io/badge/license-Apache--2.0-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/getzep/zep-context-plugin?style=flat-square)

Distributed through each host's org catalog rather than a public marketplace, the plugin adds the Zep Context MCP connection plus a skill that guides when to call it ([docs](https://help.getzep.com/context-mcp-server)).

**Key facts:** Claude Code, Codex CLI, Cursor, Claude and ChatGPT · temporal knowledge graph with per-user graphs and shared Context Graphs (project-wide or group-based access) · Free trial 10,000 credits a month with 1 MCP seat, Flex $125/mo (5 seats), Flex Plus $375/mo (15 seats) ([pricing](https://www.getzep.com/pricing)).

**Strengths**
- Enterprise access controls: OAuth 2.1, custom OIDC on Enterprise, read-only connections.
- Shared graphs for teams.

**Weaknesses**
- Explicit tool calls only; no automatic capture is described.
- MCP seats are metered, and the cheapest paid plan is $125/mo.
- The plugin repo is new (2 stars as of 2026-11-03).

**Best for:** companies that already run Zep and want its graph inside Claude Code or Codex.

### 22. Serena

[![Stars](https://img.shields.io/github/stars/oraios/serena?style=flat-square&label=stars)](https://github.com/oraios/serena)
![License](https://img.shields.io/badge/license-GPL--3.0--or--later-blue?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/oraios/serena?style=flat-square)

Memory sits next to symbol-level code tools driven by language servers; the README describes the memory system as simple and easy to disable, and says users often combine it with `AGENTS.md` ([README](https://github.com/oraios/serena)).

**Key facts:** Claude Code, Codex, OpenCode, Gemini CLI, VS Code, Cursor and JetBrains assistants, Claude Desktop · GPL-3.0-or-later for the app, MIT for SolidLSP · the star count reflects the whole coding toolkit, not the memory feature.

**Strengths**
- One server gives an agent both code navigation and project memory.

**Weaknesses**
- Memory is a minor feature, written only when the agent calls a tool.
- GPL license for the app.

**Best for:** Serena users who want light project notes without another plugin.

### 23. Pieces

![Source](https://img.shields.io/badge/source-closed-lightgrey?style=flat-square)

The Long-Term Memory engine in PiecesOS captures workflow context at the operating-system level and processes it on the device; coding agents query it through the `ask_pieces_ltm` MCP tool, with one-click setup for Cursor and VS Code ([docs](https://docs.pieces.app/products/mcp)).

**Key facts:** closed source, local desktop app · Pro $18.99/user/mo, Enterprise $22.99/user/mo with org-governed memory, 7-day trial with a card ([pricing](https://pieces.app/pricing)).

**Strengths**
- Capture runs without any agent hooks.
- Data stays on the device.

**Weaknesses**
- Closed source, and PiecesOS has to be running.
- Recall is an MCP tool the agent must decide to call.
- No free tier listed.

**Best for:** developers who want one desktop-wide memory shared by every tool they use.

### 24. Cline Memory Bank

[![Stars](https://img.shields.io/github/stars/nickbaumann98/cline_docs?style=flat-square&label=origin%20repo%20stars)](https://github.com/nickbaumann98/cline_docs)

Cline's official docs pattern: custom instructions in `.clinerules/memory-bank.md` tell Cline it "MUST read ALL memory bank files at the start of EVERY task" from six Markdown files in `memory-bank/` ([Cline docs](https://docs.cline.bot/prompting/cline-memory-bank)).

**Key facts:** files are `projectbrief`, `productContext`, `activeContext`, `systemPatterns`, `techContext` and `progress` · saying "update memory bank" triggers a rewrite · free, in the repo · the pattern is kept in Cline's docs; the origin repo has had no push since 2025-06-10.

**Strengths**
- Zero dependencies, versionable files.
- Documented by the Cline team.

**Weaknesses**
- Updates depend on you asking for them, and when the context fills you update and restart by hand.
- Reading every file on every task costs tokens.

**Best for:** Cline users who want a shared, reviewable project brief in the repo.

## Built-in agent memory (not ranked)

Every major agent now ships some memory of its own. These are not plugins, so they are not ranked, but they decide whether you need one.

| Agent | Built-in memory | Who writes it | Where it lives | Shared with the team | Default |
|---|---|---|---|---|---|
| Claude Code | `CLAUDE.md` (managed, user, project, `CLAUDE.local.md`; can read `AGENTS.md`) | You | In the repo, user folder or managed policy | Yes, through git or org-managed policy | Loaded every session |
| Claude Code | Auto memory (`user`, `feedback`, `project`, `reference` notes) | Claude | `~/.claude/projects/<project>/memory/`, shared across worktrees | No, per user and machine | On in local sessions; first 200 lines or 25KB load |
| Codex | Memories | Codex, in the background after chats go idle | `$CODEX_HOME/memories_v2/` | No, tied to the machine | Off; `memories = true` under `[features]` |
| GitHub Copilot | Copilot Memory (repo facts and user preferences) | Copilot, from users with write access | GitHub | Yes, repo facts are shared with collaborators | Paid plans; facts expire after 90 days by default (7 to 180 configurable) |
| Cursor | Rules: Project (`.cursor/rules/*.mdc`), User, Team, `AGENTS.md` | You | Repo, user settings, team dashboard | Team rules on Team and Enterprise plans | The Memories management UI was removed in 2.1.x |
| Windsurf (Devin Desktop) | Cascade memories | Cascade | `~/.codeium/windsurf/memories/`, per workspace | No, not committed | Per search excerpts of older docs; current docs cover rules only |
| Gemini CLI | `GEMINI.md` (global, project, subdirectory) plus experimental Auto Memory | You, or the CLI when asked to remember | `~/.gemini/GEMINI.md` and project files | Project files through git | GEMINI.md loads; Auto Memory is experimental |

Sources: [Claude Code memory](https://code.claude.com/docs/en/memory), [Codex memories](https://learn.chatgpt.com/docs/customization/memories?surface=app), [Copilot Memory](https://docs.github.com/en/copilot/concepts/agents/copilot-memory), [Cursor rules](https://cursor.com/docs/context/rules) and [forum](https://forum.cursor.com/t/memories-not-showing/143820), [Windsurf memories](https://docs.windsurf.com/windsurf/cascade/memories.md), [Gemini CLI memory](https://geminicli.com/docs/cli/tutorials/memory-management/).

A few details that matter when choosing:

- Codex's own docs say to "Keep required team guidance in `AGENTS.md` or checked-in documentation", because memories stay on one machine.
- Copilot Memory is the only built-in with repo-level memory shared across a team by default, and it checks citations before using a fact.
- Cursor staff gave conflicting answers about Memories: one said it was removed with an export path to Rules, a later reply said only the management UI went away.
- Gemini CLI's docs carry a banner saying it was replaced by Antigravity CLI for unpaid and Google One users.

Built-ins cover per-user notes well. The plugins above earn their place with cross-agent memory, team sharing, full-transcript search and recall on every prompt.

## Deprecated or not recommended

Not counted in the 24.

- **[ByteRover CLI](https://github.com/campfirein/byterover-cli) (formerly Cipher) and [brv-claude-plugin](https://github.com/campfirein/brv-claude-plugin):** the CLI repo is archived on GitHub (last commit 2026-06-25) with no public explanation, it is licensed under the Elastic License 2.0 (source-available, not OSI), and the plugin's recall hook can block a prompt for 6 to 8 seconds. The npm package is still published.
- **Hindsight `hindsight-memory` Claude Code plugin:** retired; Vectorize points to `@vectorize-io/hindsight-coding-agents` (entry 4).
- **[mem0ai/mem0-mcp](https://github.com/mem0ai/mem0-mcp):** archived. Use the Mem0 plugin (entry 6) instead.
- **[Roo Code Memory Bank](https://github.com/GreatScottyMac/roo-code-memory-bank):** no commit since 2025-05-15.
- **[alioshr/memory-bank-mcp](https://github.com/alioshr/memory-bank-mcp):** no push since 2025-08-20.
- **[coleam00/mcp-mem0](https://github.com/coleam00/mcp-mem0):** a template with no push since 2025-04-13.
- **[ConPort](https://github.com/GreatScottyMac/context-portal):** no push since 2026-01-27, and Claude Code is not among its documented clients.
- **[Cursor Memory Bank](https://github.com/vanzan01/cursor-memory-bank):** no commit since 2026-01-07 and no release since 2025-12-05, and it has no license file.

## FAQ

### How do I give Claude Code persistent memory between sessions?

Claude Code already has two layers: `CLAUDE.md`, which you write, and auto memory, which Claude writes to `~/.claude/projects/<project>/memory/` and loads each session. A memory plugin adds hooks that record each turn and inject past context automatically: install Glen with `npx @tryglen/cli@latest install`, or claude-mem with `npx claude-mem install`, or any plugin above with `/plugin install`.

### What are the best claude-mem alternatives?

Supermemory if you want recall on every prompt across four agents; agentmemory or deja-vu if you want local hooks with no API key; Hindsight if you use many agents on one repo; Glen if the memory should be shared by a team. claude-mem's installer starts a hosted observer by default, so check that setting whichever you pick.

### Is CLAUDE.md or auto memory enough?

For one person on one machine, often yes. Both are local and per user (CLAUDE.md can be shared through git, but you maintain it by hand). Plugins add what built-ins lack: memory that follows you across agents, memory shared with teammates, search over full past transcripts, and recall injected on every prompt.

### Shared team memory for coding agents: which plugins support it?

Glen (one org memory, access checked per observation), Mem0 (a shared project pool), Supermemory (a team-named namespace), Hindsight Cloud, Basic Memory Teams, claude-mem's opt-in TeamBrain, and the Zep Context plugin (shared graphs). Self-hosted options: mcp-memory-service (HTTP sync), Beads (Dolt remotes), Engram (Git Sync) and projectmem (files committed to the repo).

### Plugin hooks vs MCP tools: which remembers more reliably?

Hooks. A hook runs on every session start, prompt or stop whether or not the model thinks about memory; an MCP tool runs only when the model decides to call it. Within hook plugins, recall on every prompt (Glen in Claude Code, Codex and pi; Supermemory; Cognee) catches more than recall on the first prompt only (Mem0, Hindsight by default).

### Do memory plugins work across agents?

Many do. Hindsight covers 13 agents, claude-mem's installer about a dozen, agentmemory and Nowledge Mem a similar range, Supermemory four, Episodic Memory five. Glen has plugins for Claude Code, Codex, Cursor, Grok Build CLI, jcode and pi, and any MCP client can search it.

### Which memory plugins send my code or prompts to a cloud?

By default: Glen, Supermemory, Mem0, Hindsight (cloud mode), Claude Subconscious (Letta Cloud unless self-hosted), the Zep Context plugin, and claude-mem's default hosted observer. Local by default: agentmemory, deja-vu, projectmem, MemPalace, Episodic Memory (though summarization uses your Claude or Codex account), memsearch, Engram, Basic Memory and Cognee's local mode (which still calls your LLM provider for extraction).

### What is the best memory plugin for Codex or Cursor?

For Codex with hooks on every prompt: Glen. Others with Codex hooks or plugins: Hindsight, agentmemory, Mem0, Cognee, mcp-memory-service, MemPalace and Episodic Memory. For Cursor: Glen, agentmemory and MemPalace capture automatically; Supermemory has a young Cursor plugin.

## Related

- [Best Agent Memory MCP](https://github.com/Glen-Web-App/best-agent-memory-mcp): the companion list, ranking 25 memory MCP servers (hosted and open source) for Claude Code, Cursor, Codex and any MCP client.

## Contributing

Additions and corrections are welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) first: entries must be maintained, must ship a memory plugin for a coding agent, and every fact needs a source link.

## License

[CC0-1.0](LICENSE). To the extent possible under law, the contributors have waived all copyright and related rights to this list.

Last updated: November 2026
