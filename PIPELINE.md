# Zovo AI Agentic Pipeline — Complete System Documentation

**Version:** v4.0 (GitHub SEO Smart Fleet)
**Last Updated:** 2026-03-12
**Author:** theluckystrike
**Status:** Production — 2,365+ articles deployed, 75 agents active

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [System Architecture](#2-system-architecture)
3. [Directory Structure](#3-directory-structure)
4. [Agent System](#4-agent-system)
5. [State Management](#5-state-management)
6. [Content Generation Flow](#6-content-generation-flow)
7. [Merge System](#7-merge-system)
8. [QA & Verification Layer](#8-qa--verification-layer)
9. [GitHub Pages Deployment](#9-github-pages-deployment)
10. [Configuration & Authentication](#10-configuration--authentication)
11. [Fleet Manifest & Versions](#11-fleet-manifest--versions)
12. [Keyword Strategy](#12-keyword-strategy)
13. [Operational Metrics](#13-operational-metrics)
14. [Monitoring & Logs](#14-monitoring--logs)
15. [Process Management](#15-process-management)
16. [Business & Service Layer](#16-business--service-layer)
17. [Zovo Ecosystem](#17-zovo-ecosystem)
18. [npm Packages & SEO Funnel](#18-npm-packages--seo-funnel)
19. [Extension Engine Relationship](#19-extension-engine-relationship)
20. [Known Gaps & Expansion Points](#20-known-gaps--expansion-points)

---

## 1. Executive Summary

The Zovo AI Agentic Pipeline is a fully autonomous content generation and SEO deployment system. It uses 75 MiniMax M2.5 AI agents running in parallel on a local Mac to produce SEO-optimized articles, push them to GitHub via SSH, merge them via the GitHub API, and deploy them as individually indexed pages on GitHub Pages (DR97 domain authority).

**Core thesis:** GitHub Pages has Domain Rating 97. Every markdown file with Jekyll front matter becomes an individually Google-indexed page. A repo with 2,365 articles = 2,365+ potential search results on a DR97 domain, for $0 hosting cost.

### Key Numbers (as of 2026-03-12)

| Metric | Value |
|--------|-------|
| Articles on main | 2,365 |
| Active agent slots | 75 |
| Agents running at observation | 55 |
| Merge throughput (peak) | 107/hour |
| Merge throughput (sustained) | ~80/hour |
| Conflict rate | 2.2% |
| Total merges logged | 612+ |
| Refill script versions | 15 |
| Total topics dispatched (all batches) | ~1,100+ unique keywords |
| Repo age | 3 days (created 2026-03-09) |
| Repo size | 52.6 MB |
| Workspace disk usage | 3.1 GB |
| GitHub API usage | ~400 calls/hour (of 5,000 limit) |

---

## 2. System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    ORCHESTRATION LAYER                       │
│                                                             │
│  refill-v{N}.sh          merge-api.sh         Gemini QA     │
│  (task dispatcher)       (branch merger)      (5 workers)   │
│  polls every 30s         polls every 30s      tmux gq:1-5   │
└────────┬────────────────────┬──────────────────────┬────────┘
         │                    │                      │
         ▼                    ▼                      ▼
┌─────────────────┐  ┌──────────────────┐  ┌─────────────────┐
│  STATE LAYER    │  │  GITHUB API      │  │  QA WORKSPACE   │
│                 │  │                  │  │                 │
│  terminal-a1.md │  │  POST /merges    │  │  gemini-qa-1/   │
│  terminal-a2.md │  │  DELETE /refs    │  │  gemini-qa-2/   │
│  ...            │  │  GET /branches   │  │  ...            │
│  terminal-a75.md│  │                  │  │  gemini-qa-5/   │
│  agent-status.md│  │                  │  │                 │
└────────┬────────┘  └──────────────────┘  └─────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────┐
│                    EXECUTION LAYER                           │
│                                                             │
│  75 mini-agent processes (MiniMax M2.5)                     │
│  Each in isolated workspace: zovo-workspaces/a{N}/          │
│  Tools: bash, read_file, write_file, edit_file              │
│                                                             │
│  a1 ──► clone repo ──► create branch ──► write article      │
│  a2 ──► clone repo ──► create branch ──► write article      │
│  ...                                                        │
│  a75 ──► clone repo ──► create branch ──► write article     │
└────────┬────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────┐
│                    DEPLOYMENT LAYER                          │
│                                                             │
│  GitHub Pages (Jekyll) ──► theluckystrike.github.io/chrome-tips │
│  Auto-rebuilds on every merge to main                       │
│  DR97 domain, $0 hosting, individually indexed pages        │
└─────────────────────────────────────────────────────────────┘
```

### Three-Engine Design

| Engine | Role | Count | Model |
|--------|------|-------|-------|
| MiniMax | Volume content writer | 75 agents | MiniMax-M2.5 |
| Gemini | QA, SEO audit, internal links | 5 workers | Gemini CLI |
| Claude | PM orchestration, code review | 3 PMs (fleet v4) | Claude Code |

---

## 3. Directory Structure

### Pipeline Root: `/Users/mike/zovo-oss/`

```
zovo-oss/
├── chrome-tips/              # Bare git repo stub (.git only)
│   └── .git/
└── state/                    # Task dispatch + status (THE CORE)
    ├── terminal-a1.md        # Task file for agent a1
    ├── terminal-a2.md        # Task file for agent a2
    ├── ...                   # (75 files total, a1–a75)
    ├── terminal-a75.md       # Task file for agent a75
    ├── agent-status.md       # Shared append-only activity log
    └── agent-status-a36.md   # Per-agent status snapshot (example)
```

### Agent Workspaces: `/Users/mike/zovo-workspaces/`

```
zovo-workspaces/
├── a1/                       # Agent a1 isolated workspace
│   └── chrome-tips/          # Full git clone of theluckystrike/chrome-tips
├── a2/
│   └── chrome-tips/
├── ...                       # (75 per-agent directories)
├── a75/
│   └── chrome-tips/
├── chrome-tips/              # Shared merge workspace (2,365 articles)
│   ├── _config.yml           # Jekyll config
│   ├── _layouts/             # Jekyll layouts
│   ├── articles/             # 2,365 .md article files
│   ├── sitemap.xml           # Auto-generated sitemap
│   └── robots.txt            # Crawler directives
├── chrome-tips2/             # QA copy (1,930 files)
├── chrome-extension-guide/   # SEO authority site clone
└── agent-status.md           # Workspace-level status copy
```

### Orchestration Scripts: `/tmp/`

```
/tmp/
├── merge-api.sh              # PRIMARY: API-only merge loop (no clone)
├── merge-loop.sh             # LEGACY: Clone-based merge loop
├── merge-loop.log            # Merge history (625+ entries)
├── merge-api-output.log      # API error log
├── push_branch.sh            # Branch creation via curl + GitHub API
├── refill-loop.sh            # v1: 25 agents, 25 topics
├── refill-loop-v2.sh         # v2: 25 agents, 105 topics
├── refill-loop-v3.sh         # v3: 25 agents, 78 topics
├── refill-v4.sh              # v4: 75 agents, 50 topics
├── refill-v5.sh              # v5: 75 agents, 101 topics
├── refill-v6.sh              # v6: 75 agents, 72 topics
├── refill-v7.sh              # v7: 75 agents, 71 topics
├── refill-v9.sh              # v9: 75 agents, 73 topics (structured format)
├── refill-v10.sh             # v10: 75 agents, 73 topics
├── refill-v11.sh             # v11: 75 agents, 74 topics
├── refill-v12.sh             # v12: 75 agents, 71 topics
├── refill-v13.sh             # v13: 75 agents, 72 topics
├── refill-v14.sh             # v14: 75 agents, 74 topics
├── refill-v15.sh             # v15: 75 agents, 75 topics (CURRENT)
├── refill-ssh.sh             # SSH-variant, 72 topics
├── refill-v*.log             # Dispatch completion logs
├── gemini-qa-{1..5}/         # Gemini QA agent workspaces
└── gemini-qa-merge{1..3}/    # Gemini merge agent workspaces
```

### Fleet Launchers: `~/Downloads/`

```
~/Downloads/
├── fleet-seo-v2/
│   └── fleet-seo-launcher.sh    # v2: 25 MiniMax + 3 Gemini + 1 Claude PM
└── github-seo-smart-fleet/
    ├── launch.sh                # v4: 25 MiniMax + 3 Gemini + 3 Claude PMs
    ├── status.sh                # Fleet status checker
    └── stop.sh                  # Fleet stopper (tmux kill + sentinel file)
```

### Mini-Agent Runtime: `~/.mini-agent/`

```
~/.mini-agent/
├── config/
│   ├── config.yaml              # MiniMax API key + model config
│   ├── mcp.json                 # MCP tools (search + memory, both disabled)
│   └── system_prompt.md         # Default agent system prompt
└── log/
    └── agent_run_*.log          # 232+ full agentic run logs (JSON)
```

---

## 4. Agent System

### What Is a Mini-Agent

Mini-Agent is an open-source CLI tool from MiniMax-AI, providing an agentic loop around the MiniMax M2.5 LLM.

**Binary:** `/Users/mike/.local/bin/mini-agent` (symlink via uv)
**Runtime:** Python 3.10, installed via uv (Astral's fast Python package manager)
**Invocation:**
```bash
mini-agent --workspace ~/zovo-workspaces/a{N} --task "..."
```

### Agent Tools Available

| Tool | Purpose |
|------|---------|
| `bash` | Shell command execution (cwd = workspace) |
| `bash_output` | Read stdout of background bash commands |
| `bash_kill` | Kill background processes |
| `read_file` | Read files (workspace-relative or absolute) |
| `write_file` | Write files |
| `edit_file` | Edit files |
| `record_note` | Write to `.agent_memory.json` in workspace |
| `get_skill` | Load specialized skill guidance |

### Agent User Prompt (per run)

```
You are a{N}, a task executor. GitHub account: theluckystrike.
git config user.name 'theluckystrike' && git config user.email '51033404+theluckystrike@users.noreply.github.com'

YOUR TASK (assigned by the project manager):
{contents of terminal-a{N}.md}

RULES:
- Execute the task EXACTLY as described above.
- Push to the BRANCH specified in the task. NEVER push to main.
- ONLY work on repos owned by theluckystrike. Verify before push.
- IMPORTANT: When cloning repos, use SSH: git clone git@github.com:theluckystrike/REPONAME.git
- Also set the remote: git remote set-url origin git@github.com:theluckystrike/REPONAME.git
- ONE task per run. When done, stop.
- If something fails, log the error to ~/zovo-oss/state/agent-status.md and stop.

Log completion to agent-status.md as a{N}. Go.
```

### Agent Execution Flow

```
1. Agent reads task from terminal-a{N}.md
2. Clones git@github.com:theluckystrike/chrome-tips.git (or uses existing clone)
3. Creates branch: content/a{N}-{keyword-slug}
4. Writes article to articles/{slug}.md (800-1500 words, Jekyll front matter)
5. git add . && git commit -m "Add article: {keyword}"
6. git push origin content/a{N}-{slug}
7. Appends completion to ~/zovo-oss/state/agent-status.md
8. Clears its task file (terminal-a{N}.md becomes empty)
```

---

## 5. State Management

### The Task Queue Protocol

The state management system is a dead-simple file-based queue. No message broker, no database, no IPC.

**One file per agent:** `~/zovo-oss/state/terminal-a{N}.md`

| File State | Meaning |
|-----------|---------|
| Content (> 5 bytes) | Agent has a task to execute |
| Empty (0-5 bytes) | Agent is idle, waiting for dispatch |

### Task File Format (v9+)

```
REPO: theluckystrike/chrome-tips
BRANCH: content/a{N}-{slug}
FILE: articles/{slug}.md
KEYWORD: "{keyword phrase}"
Write a helpful 800-1500 word article targeting the keyword above.
Include Jekyll front matter (layout: default, title, description).
Mention Tab Suspender Pro naturally once.
End with: Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
Avoid: delve, landscape, it's important to note, let's dive in, in today's digital world.
```

### Slug Generation

```bash
SLUG=$(echo "$KEYWORD" | tr ' ' '-' | tr -cd 'a-z0-9-')
```

### Agent Status Logging

Agents append heartbeats to `~/zovo-oss/state/agent-status.md`:
```
a43: 2026-03-12T03:38:37Z EXIT run #8
a58: 2026-03-12T03:38:44Z EXIT run #6
a3: 2026-03-12T03:38:45Z EXIT run #8
```

Some agents write structured completion reports:
```
Agent: a41 — chrome-http2-multiplexing-explained — COMPLETED
  Words: 1100
  Branch: content/a41-chrome-http2-multiplexing-explained
  Commit: 31b2aafff
```

### Stop Signal

Creating `~/zovo-oss/state/stop-agents` causes all agent scripts to exit gracefully on their next poll cycle.

---

## 6. Content Generation Flow

### Dispatch Algorithm (all refill scripts)

```bash
STATE_DIR=~/zovo-oss/state
TOPICS=( "keyword1" "keyword2" ... )  # 70-75 per batch
IDX=0

while [ $IDX -lt ${#TOPICS[@]} ]; do
  for i in $(seq 1 75); do
    SIZE=$(wc -c < "$STATE_DIR/terminal-a${i}.md" | tr -d ' ')
    if [ "$SIZE" -lt 5 ]; then
      KEYWORD="${TOPICS[$IDX]}"
      SLUG=$(echo "$KEYWORD" | tr ' ' '-' | tr -cd 'a-z0-9-')
      cat > "$STATE_DIR/terminal-a${i}.md" << EOF
REPO: theluckystrike/chrome-tips
BRANCH: content/a${i}-${SLUG}
FILE: articles/${SLUG}.md
KEYWORD: "${KEYWORD}"
Write a helpful 800-1500 word article targeting the keyword above.
Include Jekyll front matter (layout: default, title, description).
Mention Tab Suspender Pro naturally once.
End with: Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
Avoid: delve, landscape, it's important to note, let's dive in, in today's digital world.
EOF
      IDX=$((IDX + 1))
      [ $IDX -ge ${#TOPICS[@]} ] && break
    fi
  done
  sleep 30
done
echo "All ${#TOPICS[@]} topics dispatched!"
```

### Article Output Format

```yaml
---
layout: post
title: "Human-readable SEO title"
description: "150-160 character SEO description targeting the keyword"
date: 2026-03-12
last_modified_at: '2026-03-12'
permalink: chrome-keyword-slug
categories:
- performance
- browsers
tags:
- chrome
- optimization
author: theluckystrike
---

# Article Title Targeting the Keyword

[3-7 H2 sections with practical step-by-step content, 800-1500 words]

[Tab Suspender Pro mentioned naturally once within the content]

## Final Thoughts

[Wrap-up paragraph]

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
```

### Content Quality Rules

| Rule | Details |
|------|---------|
| Word count | 800-1500 words |
| Front matter | Jekyll: layout, title, description, date, permalink |
| Product mention | Tab Suspender Pro, once, naturally integrated |
| Footer | `Built by theluckystrike — More tips at [zovo.one](https://zovo.one)` |
| Forbidden phrases | `delve`, `landscape`, `it's important to note`, `let's dive in`, `in today's digital world` |

### Refill Script Evolution

| Version | Agents | Topics | Focus Area |
|---------|--------|--------|-----------|
| v1 (loop) | 25 | 25 | Basic Chrome settings (pdf, bookmarks, tabs) |
| v2 | 25 | 105 | Web APIs (prerender, WebGPU, WASM, passkeys) |
| v3 | 25 | 78 | User-facing slow PC / low RAM problems |
| v4 | 75 | 50 | Chrome 2026 AI features, browser comparisons |
| v5 | 75 | 101 | Error codes (ERR_*), extension API reference |
| v6 | 75 | 72 | PWA, Privacy Sandbox (CHIPS, fenced frames, FLEDGE) |
| v7 | 75 | 71 | Bleeding-edge: WebXR, Houdini, CSS scroll-driven animations |
| v9 | 75 | 73 | General troubleshooting + DevTools |
| v10 | 75 | 73 | Crashes, enterprise, DevTools deep dive |
| v11 | 75 | 74 | Privacy Sandbox detailed, modern CSS, View Transitions |
| v12 | 75 | 71 | Performance APIs, Core Web Vitals, automation |
| v13 | 75 | 72 | HTTP/2, HTTP/3, QUIC, image formats, workers |
| v14 | 75 | 74 | Low-end hardware, benchmarks, family/enterprise |
| v15 | 75 | 75 | macOS-specific, extension dev APIs, MV3 migration |
| ssh | 75 | 72 | Mixed Chrome performance + Web Vitals + PWA |

---

## 7. Merge System

### Primary: API-Only Merge (`/tmp/merge-api.sh`)

Runs entirely without cloning the repo. All operations go through the GitHub REST API via `gh`.

```bash
#!/bin/bash
while true; do
  BRANCHES=$(gh api repos/theluckystrike/chrome-tips/branches \
    --paginate \
    --jq '.[] | select(.name | startswith("content/")) | .name' 2>/dev/null)

  if [ -n "$BRANCHES" ]; then
    for b in $BRANCHES; do
      RESULT=$(gh api repos/theluckystrike/chrome-tips/merges \
        -f base=main -f head="$b" \
        -f commit_message="Merge $b" 2>&1)

      if echo "$RESULT" | grep -q '"sha"'; then
        # Success — delete branch
        gh api -X DELETE \
          "repos/theluckystrike/chrome-tips/git/refs/heads/$(echo "$b" | sed 's|/|%2F|g')" \
          2>/dev/null
        echo "$(date +%H:%M) merged $b" >> /tmp/merge-loop.log
      elif echo "$RESULT" | grep -q "Merge conflict"; then
        # Conflict — log and delete branch (content lost)
        echo "$(date +%H:%M) CONFLICT $b — skipping" >> /tmp/merge-loop.log
        gh api -X DELETE \
          "repos/theluckystrike/chrome-tips/git/refs/heads/$(echo "$b" | sed 's|/|%2F|g')" \
          2>/dev/null
      fi
      sleep 1    # Throttle between merges
    done
  fi
  sleep 30       # Poll every 30 seconds
done
```

### Legacy: Clone-Based Merge (`/tmp/merge-loop.sh`)

Uses a persistent local clone at `/tmp/mm-merge-persist`:
```bash
git merge "origin/$b" --no-edit -X theirs   # Agent content wins on conflict
git push origin main
git push origin --delete "$b"
```

### GitHub API Endpoints Used

| Purpose | Method | Endpoint |
|---------|--------|----------|
| List branches | GET | `/repos/theluckystrike/chrome-tips/branches` |
| Merge branch to main | POST | `/repos/theluckystrike/chrome-tips/merges` |
| Delete branch ref | DELETE | `/repos/theluckystrike/chrome-tips/git/refs/heads/{branch}` |
| Create branch ref | POST | `/repos/theluckystrike/chrome-tips/git/refs` |
| File tree (count) | GET | `/repos/theluckystrike/chrome-tips/git/trees/main?recursive=1` |
| Pages config | GET | `/repos/theluckystrike/chrome-tips/pages` |

### Branch Naming Strategy

| Prefix | Purpose | Merge Handling |
|--------|---------|---------------|
| `content/a{N}-{slug}` | AI-written articles (primary pipeline) | Auto-merged by merge-api.sh |
| `consumer/a{N}-{slug}` | Consumer-facing articles (different tone) | Manual/separate merge |
| `qa/round{N}-batch-{N}` | QA review batches | Manual/separate merge |
| `seo/internal-links-*` | Internal link building batches | Manual/separate merge |
| `fix/*` | Hotfix branches | Manual merge |

### Conflict Resolution Strategy

| Merge Script | Strategy |
|-------------|----------|
| merge-api.sh (v1) | Log conflict, **delete branch anyway** (content lost, regenerated later) |
| merge-loop.sh (v2) | `git merge -X theirs` (agent content always wins) |

**Rationale:** At scale, losing one article to a conflict is cheaper than blocking the queue. Refill scripts will simply regenerate more content.

---

## 8. QA & Verification Layer

### Gemini QA Workers (tmux session `gq`)

5 Gemini CLI agents run in tmux windows `gq:gq1` through `gq:gq5`:

| Worker | Workspace | Task |
|--------|-----------|------|
| gq1 | `/tmp/gemini-qa-1/` | Fix YAML frontmatter (title, description, date, permalink) |
| gq2 | `/tmp/gemini-qa-2/` | Add `## Related Articles` sections with internal links |
| gq3 | `/tmp/gemini-qa-3/` | Verify word count >= 800, remove forbidden phrases |
| gq4 | `/tmp/gemini-qa-4/` | Add Tab Suspender Pro mention if missing |
| gq5 | `/tmp/gemini-qa-5/` | Fix footer line if missing or malformed |

**QA Agent Task Files:**
- `GEMINI.md` in each workspace — the agent's assignment
- `my_range.txt` / `my_assigned_files.txt` — which articles to process
- `current_batch.txt` — batch tracking

**QA Commit Pattern:**
```
seo: add internal links batch-N
qa: fix frontmatter batch-N
```

**QA branches:** `qa/round3-batch-{N}`, `qa/loop-{N}`

### Quality Checks Performed

1. YAML frontmatter completeness (title, description 150-160 chars, date, last_modified_at, permalink)
2. Word count >= 800
3. Forbidden phrase removal (5 AI-tell phrases)
4. Tab Suspender Pro mention present
5. Footer line present and correct
6. Related Articles section with internal links to other articles

---

## 9. GitHub Pages Deployment

### Configuration

| Setting | Value |
|---------|-------|
| Build type | `legacy` (Jekyll, not GitHub Actions) |
| Source | `main` branch, root `/` |
| URL | `https://theluckystrike.github.io/chrome-tips/` |
| HTTPS | Enforced |
| Custom domain | None |
| Theme | Minima |
| Plugins | `jekyll-seo-tag`, `jekyll-sitemap` |

### Jekyll Config (`_config.yml`)

```yaml
title: "Chrome Tips by theluckystrike"
description: "Practical Chrome browser tips for speed, memory, and productivity"
url: "https://theluckystrike.github.io"
baseurl: "/chrome-tips"
theme: minima
include:
  - b4e8f2a1c7d94e6fab3209d1e5c8a7f6.txt    # Google Search Console verification
plugins:
  - jekyll-seo-tag
  - jekyll-sitemap
```

### How Deployment Works

Every merge to `main` automatically triggers a GitHub Pages rebuild. No deploy scripts, webhooks, or GitHub Actions needed. Jekyll processes all `.md` files with front matter and generates static HTML.

### Supporting Files

- `robots.txt` — allows all crawlers, points to sitemap
- `sitemap.xml` — dynamically generated from `site.pages`, includes lastmod from frontmatter
- `Gemfile` — `gem "github-pages"` (standard GitHub Pages bundle)

---

## 10. Configuration & Authentication

### MiniMax API (`~/.mini-agent/config/config.yaml`)

```yaml
api_key: "sk-cp-..."
api_base: "https://api.minimax.io"
model: "MiniMax-M2.5"
```

### SSH Authentication

**Key:** `~/.ssh/id_ed25519` (Ed25519)
**Public key:** `ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDayCC0DUsiLAV8pdn2IAhe9DV+ILfVzH4gD6PM5NjAQ theluckystrike`

**SSH Config (`~/.ssh/config`):**
```
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519
    AddKeysToAgent yes
    IdentitiesOnly yes
```

**SSH Agent:** 8 active sockets under `~/.ssh/agent/` (one per concurrent thread)

### Git Config (Global)

```
user.name = theluckystrike
user.email = 51033404+theluckystrike@users.noreply.github.com
credential.helper = store
init.defaultbranch = main
```

### GitHub Authentication

- Token type: Classic (`ghp_`)
- Scope: Full repo + admin
- Used by: `gh` CLI for all API calls

---

## 11. Fleet Manifest & Versions

### Fleet v4.0 — GitHub SEO Smart Fleet (Current)

**Launcher:** `~/Downloads/github-seo-smart-fleet/launch.sh`
**tmux session:** `sf`
**Total workers:** 31

| # | Role | Engine | Scope |
|---|------|--------|-------|
| 0 | PM1 | Claude Code | Jekyll + SEO, manages a1-a10 |
| 1 | PM2 | Claude Code | Content + Templates, manages a11-a25 |
| 2 | PM3 | Claude Code | Gemini management + branch merging |
| 3-7 | Pod 1-5 | MiniMax x25 | a1-a25 (staggered launch) |
| 8 | G1 | Gemini | npm SEO |
| 9 | G2 | Gemini | Quality audit |
| 10 | G3 | Gemini | Template builds |

**Staggered pod starts:** Pod1 immediate, Pod2 +2 min, Pod3 +4 min, Pod4 +1 min, Pod5 +3 min

**Design features:**
- `unset CLAUDECODE` for nested Claude sessions
- Atomic task writes (`.tmp` file + `mv` to prevent partial reads)
- PM phase state recovery files (`pm1-phase.txt`, `pm2-phase.txt`)

### Fleet v2.0 — Fleet SEO

**Launcher:** `~/Downloads/fleet-seo-v2/fleet-seo-launcher.sh`
**tmux session:** `seo`
**Total workers:** 29

| Component | Count |
|-----------|-------|
| MiniMax agents | 25 |
| Gemini agents | 3 |
| Claude PM | 1 |

### Current Active Fleet (Observation)

**75 MiniMax agents** (scaled beyond original 25-agent fleet design)
**5 Gemini QA workers** in tmux `gq`
**1 merge-api.sh** loop
**1 refill-v15.sh** dispatcher

---

## 12. Keyword Strategy

### Topic Clusters Across All 15 Refill Versions

| Cluster | Example Keywords | Versions |
|---------|-----------------|----------|
| Slow PC / Low RAM | "chrome using all my ram 4gb laptop fix", "chrome slow on 2gb ram" | v3, v9, v14 |
| Mac-Specific | "chrome eating battery macbook pro fix", "chrome helper gpu process mac" | v15 |
| Error Codes | "chrome err too many redirects fix", "chrome err quic protocol error" | v5 |
| Tab Management | "chrome tab discarding vs suspending", "best tab management extension" | v1, v9 |
| Browser Comparisons | "chrome vs brave memory comparison", "chrome vs edge 2026" | v4, v14 |
| DevTools | "chrome performance profiling beginners", "chrome coverage tab unused css" | v9, v10, v12 |
| Extensions | "chrome extension malware signs", "chrome extension monetization 2024" | v5, v12 |
| MV3 / Extension Dev | "chrome manifest v3 migration guide", "chrome declarative net request api" | v5, v15 |
| Privacy Sandbox | "chrome topics api vs floc", "chrome attribution reporting api" | v6, v11 |
| Web APIs (Advanced) | "chrome webgpu api graphics", "chrome webtransport api explained" | v2, v7 |
| PWA | "chrome pwa install from browser", "chrome workbox service worker" | v6, v13 |
| Modern CSS | "chrome container queries responsive", "chrome has selector css parent" | v7, v11 |
| Performance APIs | "chrome largest contentful paint optimize", "chrome interaction to next paint" | v11, v12 |
| AI Features (2026) | "chrome gemini integration how to use", "chrome built in ai writing help" | v4 |
| Security | "chrome passkeys explained", "chrome enhanced safe browsing" | v2, v14 |
| HTTP/Networking | "chrome http2 multiplexing", "chrome http3 quic protocol", "chrome early hints 103" | v13 |
| Image/Media | "chrome avif image format support", "chrome webp vs avif comparison" | v13 |
| Workers/Storage | "chrome shared worker vs service worker", "chrome cache api vs http cache" | v13 |
| Enterprise/Corporate | "chrome dlp data loss prevention", "chrome group policy deployment" | v14, v15 |
| Benchmarks | "chrome speedometer benchmark", "chrome jetstream benchmark" | v14 |

### Keyword Generation Pattern

Each batch targets ~70-75 long-tail keywords with clear search intent:
- "how to fix" / "how to enable" / "how to use" (problem-solving)
- "vs" comparisons (decision-making)
- "explained" / "guide" (educational)
- "best" / "top" (listicle-adjacent)

---

## 13. Operational Metrics

### Throughput

| Metric | Value |
|--------|-------|
| Peak merge rate | 107 merges/hour |
| Sustained merge rate | ~80 merges/hour |
| Estimated capacity | ~1,280 articles/day (16 active hours) |
| Actual 17-hour output | 612 articles merged |
| Agent run time per article | ~5-10 minutes (estimated from run counters) |

### Merge Statistics

| Metric | Value |
|--------|-------|
| Total merges logged | 612 |
| Conflicts | 14 |
| Conflict rate | 2.2% |
| Conflict handling | Branch deleted (content lost, regenerated) |

### GitHub API Usage

| Metric | Value |
|--------|-------|
| Rate limit | 5,000/hour |
| Typical usage | ~400 calls/hour (8.2%) |
| Headroom | 91.8% remaining |

### Disk Usage

| Path | Size |
|------|------|
| Pipeline control (`zovo-oss/`) | 20 MB |
| Agent workspaces (`zovo-workspaces/`) | 3.1 GB |
| Agent logs (`~/.mini-agent/log/`) | 232+ files, varies |

---

## 14. Monitoring & Logs

### Log Locations

| Source | Path | Content |
|--------|------|---------|
| Merge events | `/tmp/merge-loop.log` | `HH:MM merged content/...` or `CONFLICT` |
| Agent completions | `~/zovo-oss/state/agent-status.md` | START/EXIT heartbeats, task completions |
| Per-agent status | `~/zovo-oss/state/agent-status-a{N}.md` | Individual agent state |
| Refill dispatch | `/tmp/refill-v{N}.log` | "All N topics dispatched!" |
| Full agent traces | `~/.mini-agent/log/agent_run_*.log` | Complete JSON request/response (auditable) |
| API errors | `/tmp/merge-api-output.log` | GitHub API error responses |

### Ad-Hoc Health Check (Manual)

```bash
sleep 120 && echo "=== $(date -u +%H:%M) ===" \
  && echo "Articles: $(gh api 'repos/theluckystrike/chrome-tips/git/trees/main?recursive=1' \
      --jq '[.tree[] | select(.path | startswith("articles/")) | select(.path | endswith(".md"))] | length')" \
  && echo "Pending: $(gh api repos/theluckystrike/chrome-tips/branches --paginate \
      --jq '[.[] | select(.name | startswith("content/"))] | length')" \
  && tail -5 /tmp/merge-loop.log 2>/dev/null
```

### What Is NOT Monitored

- Per-article quality metrics (word count pass/fail, forbidden phrase violations)
- Per-agent performance (time to complete, API calls per article)
- Merge latency (time from branch push to merge)
- Article duplication detection before dispatch
- Disk usage alerts
- Agent crash details (only EXIT timestamps)
- Rate limit approach warnings
- No centralized error log
- No automated alerting of any kind

### Cron Jobs

```
0 3 * * *   find /tmp/zovo-agents -mtime +1 -delete 2>/dev/null
0 3 * * *   find ~/logs/agents -mtime +30 -delete 2>/dev/null
0 12 * * 0  ~/bin/backup-config.sh
```

---

## 15. Process Management

### Starting Agents

Each agent runs from `~/zovo-oss/agents/a{N}.sh` — shell wrapper scripts that poll `terminal-a{N}.md` every 10 seconds and invoke `mini-agent` when a task appears.

### Starting the Merge Loop

```bash
nohup /tmp/merge-api.sh &
```

### Starting the Refill Dispatcher

```bash
nohup /tmp/refill-v15.sh &
```

### Stopping Everything

**Option A — Sentinel file:**
```bash
touch ~/zovo-oss/state/stop-agents
```
All agent scripts check for this file and exit gracefully.

**Option B — Kill processes:**
```bash
ps aux | grep mini-agent | grep -v grep | awk '{print $2}' | xargs kill
kill $(cat /tmp/merge-api.pid)   # if PID tracked
kill $(cat /tmp/refill.pid)       # if PID tracked
```

**Option C — Fleet stop script:**
```bash
~/Downloads/github-seo-smart-fleet/stop.sh
```
Kills tmux session + creates `stop-agents` sentinel file.

### No Supervisor/Daemon Manager

All processes start manually and run as background daemons. No launchd, systemd, or process supervisor. No auto-restart on crash. No LaunchAgents configured for Zovo processes.

---

## 16. Business & Service Layer

### The Service: GitHub SEO Smart Fleet

**URL:** `zovo.one/services/ai-agentic-pipeline`
**Target:** Developer tool companies, open-source maintainers, developer educators
**Pricing:** $35K-$50K/month

### What the Client Gets

| Deliverable | Details |
|------------|---------|
| 31 autonomous agents | Fully modifiable, source code included |
| Full pipeline source code | Every agent script, every prompt, orchestration code |
| GitHub SEO on DR97 | Pages deployed to GitHub Pages |
| 9.5/10 quality audit score | Verified by Gemini G2 against live docs |
| ~$1,500/mo infrastructure | Dedicated server + multi-account GitHub setup |
| Dedicated engineering support | Ongoing optimization + new agents |
| tmux orchestration | Single launch command |

### Value Proposition

| Traditional SEO Agency | GitHub SEO Smart Fleet |
|-----------------------|----------------------|
| 6-12 months for 50 articles | 48 hours for 507+ pages |
| 1-2 articles/day | 7,000 AI prompts/day |
| DR 30-60 (your blog) | DR 97 (GitHub Pages) |
| $50K-$120K+/year | $35K-$50K/month |
| Content only | Full source code + pipeline |
| Linear scaling (hire more) | Deploy same fleet to new repo in 48hrs |

### The Math

Every GitHub repo is a valid target. The fleet doesn't care about content domain:
- Chrome extension guide: 507 pages
- React library docs: 312 pages
- Python SDK documentation: 284 pages
- DevOps tutorial series: 196 pages

Each deployment takes ~48 hours with the same fleet, same quality audit, different repo.

---

## 17. Zovo Ecosystem

### Brand Identity

| Element | Value |
|---------|-------|
| Primary Color | `#6C5CE7` (Zovo Purple) |
| Accent | `#00D2D3` (Teal) |
| Pro Badge | `#F59E0B` (Gold) |
| Font | Inter (400/500/600) |
| Manifest | MV3 exclusively |
| Storage prefix | `zovo_` |
| Message prefix | `ZOVO_` |
| CSS prefix | `zovo-` |

### Published Chrome Extensions (17 total)

| Extension | Users |
|-----------|-------|
| BeLikeNative | 3,430 |
| Tab Suspender Pro | 1,111 |
| JSON Formatter Pro | — |
| Clipboard History Pro | — |
| Cookie Cleaner Pro | — |
| Text Expander Pro | — |
| Quick Notes | — |
| + 10 more | — |
| **Total** | **4,700+** |

### Pricing Model

| Tier | Price |
|------|-------|
| Free | $0 (core features per extension) |
| Pro Monthly | $4.99/month (all features, all 17 extensions) |
| Pro Lifetime | $99 one-time |
| Trial | 7 days free |

### API Endpoints

| Purpose | URL |
|---------|-----|
| License verification | `https://api.zovo.one/license/verify` |
| Enterprise validation | `https://api.zovo.one/api/enterprise/validate` |

### GitHub Repos (90+ total under theluckystrike)

**Private (products):**
- `extension-engine` — 31 playbooks, build specification system
- `cookie-cleaner-pro`, `text-expander-pro`, `chrono-chambers`, `boldtake-speak-boldly`
- 5 starter template repos (React, Svelte, Popup, DevTools, Vanilla TS)

**Public (SEO + authority):**
- `chrome-tips` — 2,365 articles (this pipeline's output)
- `chrome-extension-guide` — 500+ articles
- `extension-monetization-playbook` — 30+ articles
- `theluckystrike.github.io` — GitHub Pages landing
- 30+ utility packages (storage, messaging, permissions, testing, etc.)
- Forks of popular repos (authority signals)

---

## 18. npm Packages & SEO Funnel

### Published Packages

| Package | Purpose |
|---------|---------|
| `@theluckystrike/webext-storage` | Type-safe Chrome storage with schema validation |
| `@theluckystrike/webext-messaging` | Type-safe message passing between extension contexts |
| `@theluckystrike/webext-permissions` | Runtime permission checking/requesting |
| `@theluckystrike/webext-bookmarks` | Typed bookmark helpers |
| `webext-badge` | Typed badge text/color management |
| `webext-notifications` | Typed notification wrapper |
| `chrome-ext-debugger` | Playwright + CDP testing toolkit |
| `mv3-migrate` | MV2 to MV3 CLI migration tool |
| `crx-permission-linter` | Manifest permission auditor |
| `crx-size-analyzer` | Bundle size analysis |
| `manifest-validator` | Manifest.json MV3 compliance |

### The Funnel

```
Developer searches "chrome extension storage typescript" on npm
  → finds @theluckystrike/webext-storage
  → README links to chrome-extension-guide
  → discovers Zovo extension portfolio
  → installs free extension
  → converts to Zovo Pro ($4.99/mo or $99 lifetime)
```

---

## 19. Extension Engine Relationship

The Extension Engine (`theluckystrike/extension-engine`) is the **specification layer** for building Chrome extensions. The Agentic Pipeline is the **execution layer**.

### How They Connect

```
BUILD-RULES.md (root system prompt)
  → 31 Playbooks (per-step agent briefs)
  → ARCHITECTURE.md (cross-agent shared contract)
  → cross-validate.js (machine quality gate)
  → 5-Agent pattern (Architect/Builder/Shield/Surface/Ops)
```

### 5-Agent Build Pattern

| Agent | Codename | Owns |
|-------|----------|------|
| Agent 1 | ARCHITECT | manifest.json, folder structure, module interfaces |
| Agent 2 | BUILDER | All production source code in `src/` |
| Agent 3 | SHIELD | Security, validation, CSP, XSS prevention |
| Agent 4 | SURFACE | All user-facing UI (popup, options, onboarding) |
| Agent 5 | OPS | Testing, CI/CD, locales, store assets, packaging |

### 5 Build Phases x 31 Playbooks

| Phase | Playbooks | Output |
|-------|-----------|--------|
| Foundation | 01-04 | Scaffold, manifest, shared modules, core features |
| Monetization | 05-09 | Feature gates, license system, paywall, store listing |
| Quality | 10-15 | Debug panel, tests, security audit, accessibility, crash reporter |
| Growth | 16-23 | i18n, cross-browser, referral, churn prevention, community, GDPR |
| Distribution | 24-31 | CWS compliance, esbuild bundle, 57 locales, multi-market listings |

### Quality Gate

`scripts/cross-validate.js` verifies:
- All storage keys have `zovo_` prefix
- All message actions have `ZOVO_` prefix
- All CSS classes have `zovo-` prefix
- All manifest permissions are referenced in source code

---

## 20. Known Gaps & Expansion Points

### Current Gaps (Areas to Build Out)

| Gap | Impact | Priority |
|-----|--------|----------|
| **No automated alerting** | Pipeline failures go unnoticed until manual check | High |
| **No article deduplication** | Same slug can be dispatched twice → merge conflict | High |
| **No quality scoring** | No automated word count / forbidden phrase validation pre-merge | Medium |
| **No centralized error log** | Errors scattered across agent-status.md, /tmp/*.log | Medium |
| **No process supervisor** | Agents don't auto-restart on crash | Medium |
| **Conflict = content loss** | merge-api.sh deletes conflicting branches (content lost) | Medium |
| **GitHub Pages status: errored** | Deployment may be failing due to 2,365 file Jekyll build | High |
| **No custom domain** | Running on github.io subdomain, not zovo.one | Low |
| **consumer/* branches not auto-merged** | Only `content/*` branches are handled by merge loop | Low |
| **3.1 GB workspace disk** | Each agent has full git clone; shallow clones would save space | Low |

### Expansion Opportunities

| Opportunity | Description |
|-------------|-------------|
| **Multi-repo deployment** | Same fleet targeting different repos (already designed for this) |
| **Custom domain per client** | Map GitHub Pages to client's subdomain |
| **Analytics dashboard** | Real-time view of agent status, merge rate, article count |
| **Quality scoring pipeline** | Pre-merge validation: word count, readability, SEO score |
| **A/B title testing** | Generate 2 titles per article, measure CTR via Search Console |
| **Backlink building** | Cross-link between chrome-tips, chrome-extension-guide, npm READMEs |
| **Client onboarding automation** | Script that sets up new repo + Jekyll config + first refill batch |
| **Rate limit monitoring** | Alert when approaching 5,000/hour GitHub API limit |
| **Shallow clones** | `git clone --depth 1` to reduce 3.1 GB workspace footprint |
| **LaunchAgent persistence** | Auto-start pipeline on Mac boot via launchd |
| **Webhook-based merge** | Replace polling with GitHub webhook → instant merge on push |
| **Content refresh cycle** | Re-run articles with outdated dates or deprecated APIs |

---

## Appendix A: Complete End-to-End Flow

```
STEP 1: KEYWORD SELECTION
  └─ refill-v{N}.sh contains 70-75 curated long-tail Chrome keywords

STEP 2: TASK DISPATCH (every 30 seconds)
  └─ refill script checks ~/zovo-oss/state/terminal-a{N}.md
  └─ if empty → writes structured task (REPO, BRANCH, FILE, KEYWORD, rules)

STEP 3: AGENT PICKUP
  └─ a{N}.sh detects non-empty task file
  └─ reads task, clears file
  └─ invokes: mini-agent --workspace ~/zovo-workspaces/a{N} --task "..."

STEP 4: MINIMAX M2.5 EXECUTION
  └─ Agent receives task via structured user message
  └─ Uses tools in sequence:
      bash: git clone git@github.com:theluckystrike/chrome-tips.git
      bash: git checkout -b content/a{N}-{slug}
      write_file: articles/{slug}.md (800-1500 word Jekyll article)
      bash: git add . && git commit -m "Add article: {keyword}"
      bash: git push origin content/a{N}-{slug}
  └─ Logs completion to ~/zovo-oss/state/agent-status.md

STEP 5: BRANCH MERGE (every 30 seconds)
  └─ merge-api.sh polls GitHub for content/* branches
  └─ POST /merges {base: main, head: branch}
  └─ On success → DELETE branch ref
  └─ On conflict → log + DELETE branch ref

STEP 6: QA PASS (Gemini workers)
  └─ Fix YAML frontmatter
  └─ Add Related Articles sections
  └─ Verify word count + quality rules
  └─ Commit to qa/* branch → merge to main

STEP 7: DEPLOYMENT (automatic)
  └─ GitHub Pages rebuilds Jekyll on every merge to main
  └─ Article visible at theluckystrike.github.io/chrome-tips/articles/{slug}/

STEP 8: SEO COMPOUNDING
  └─ Each page individually indexed by Google
  └─ Internal links (1,521+ connections) signal content depth
  └─ DR97 domain authority passes to every page
  └─ Traffic compounds over time as pages age and earn backlinks
```

---

## Appendix B: Key Architectural Decisions

| Decision | Implementation | Rationale |
|----------|---------------|-----------|
| File-based queue | One `.md` file per agent | Zero infrastructure, no message broker needed |
| Agent isolation | Each agent gets own workspace + git clone | No shared state corruption between agents |
| SSH for all git | `git@github.com:` everywhere | Avoids HTTPS credential issues at 75-agent scale |
| API-only merges | GitHub REST API, no local clone | Eliminates merge workspace management entirely |
| Branch-per-article | Every article on its own branch | Independent merging, no serialization bottleneck |
| Conflict = delete | Drop conflicting branch, regenerate later | Speed over completeness at scale |
| Jekyll/GitHub Pages | No hosting infra, DR97 for free | $0 cost, highest possible domain authority |
| Staggered pod starts | 1-4 minute delays between pods | Prevents SSH connection storms |
| Atomic task writes | `.tmp` + `mv` | Prevents agents from reading partial tasks |
| Sentinel stop file | `stop-agents` file = graceful shutdown | No PID tracking needed |

---

*This document describes the complete Zovo AI Agentic Pipeline as observed and operational on 2026-03-12. It is intended as the canonical reference for expanding, debugging, and selling the system.*
