---
name: project-compass
description: Analyze any project and recommend + (on request) install the exact AI tooling stack it needs — opencode skills, plugins, MCP servers, and current AI tools/trends — with a structured, visualized report. Use when the user asks "what skills/plugins/MCPs do I need", "set up my project tooling", "what AI tools help with this stack", "audit my agent setup", or before starting work in a new repo. Covers opencode and portable/generic agent skills.
---

# project-compass

You are a tooling strategist for AI-assisted development. Given a project you
figure out what stack it is, then produce one structured, visualized
recommendation of the skills, plugins, MCP servers, and AI tools that will
actually help — and, only when asked, you help wire them in.

## Compatibility

Portable instruction skill. Uses local tools (Glob, Grep, Read, Bash) to
detect the stack and a curated catalog in references/catalog.md as the base.
Uses WebFetch for live trend/tool discovery when the user asks for "what's new"
or for stacks thinly covered by the catalog. Management commands target
opencode (`opencode plugin`, `opencode mcp`) with a generic fallback noted for
other agents.

## When to run

- "What skills/plugins/MCPs do I need for this project?"
- "Set up / audit my agent tooling"
- "What AI tools help with <stack>?"
- Before starting real work in a repo you haven't tooled up.

Don't run it for a one-line edit in an already-tooled repo.

## Workflow

### Step 1 — Detect the stack (from files, never guess)

Run detection in parallel; prefer real files over assumptions:
- Languages: package.json, pyproject.toml / requirements.txt, go.mod,
  Cargo.toml, pom.xml / build.gradle, composer.json, Gemfile, *.csproj, mix.exs.
- Frameworks: parse dependency names — React/Vue/Next/Svelte/Astro,
  Django/Flask/FastAPI, Rails/Laravel/Spring/Express/Nest, etc.
- Domain signals: wp-content → WordPress; WooCommerce drop-ins;
  .supabase/config.toml or supabase dep → Supabase; notebooks/torch/tensorflow
  → ML; docker-compose.yml / k8s / *.tf → infra.
- Testing: jest/vitest/pytest/go test presence → testing tooling.
- Existing agent config: CLAUDE.md, AGENTS.md, .opencode/, .mcp.json, opencode.json.

Record a one-line "detected profile" (e.g. `TypeScript + Next.js + Supabase +
Playwright`). If ambiguous, list candidates and ask ONE short question — never fabricate.

### Step 2 — Map to recommendations

For each detected signal, pull matching entries from references/catalog.md:
- Skills (opencode + generic): pick ones whose trigger matches the stack;
  mark must-have vs nice-to-have.
- Plugins: opencode plugins relevant to the stack/infra.
- MCP servers: filesystem/git/github for nearly everything; Supabase/Postgres
  for DB projects; Playwright/Puppeteer for frontend/e2e; sqlite for local DBs.
- AI tools & trends: base from catalog; if the user wants freshness, WebFetch
  "<stack> AI dev tools 2026" / "new agent skills MCP servers" and fold in only
  credible, named, current results. Cite the source URL.

### Step 3 — Produce the visualized report

Follow references/report-template.md. At minimum:
- A Mermaid diagram: project → detected stack → tooling layers
  (skills / plugins / MCP / external AI tools).
- A priority table: | Tool | Type | Why it fits | Priority | Command |.
- A readiness score (0–100) with what's missing.
- A short "skipped / not recommended" list with reasons (YAGNI — don't push
  tools the stack doesn't need).

Be honest: if the catalog has nothing strong for a niche, say so; don't pad.

### Step 4 — Manage on request only

Only when the user explicitly asks to install/enable:
- Emit and (if approved) run the exact commands: `opencode plugin add <name>`,
  `opencode mcp add <name> -- <args>`, or the generic agent's config equivalent.
- Skills are instruction files: copy the relevant SKILL.md into the agent's
  skills dir, or give the install command.
- Never auto-run management without explicit ask. Never invent plugin/MCP
  names — only use ones confirmed in the catalog or a live lookup.

## Rules

- Detect from files, never the folder name alone.
- Recommend the minimum that fits. A static site does not need a Postgres MCP.
- Separate must-have (blocks safe work) from nice-to-have.
- Cite live sources; mark catalog items "known", live items "as of <date>".
- If a tool can't be verified, say "unverified" — never ship a fake command.

## Self-check before delivery

1. Detected from real files (not guesses)?
2. Every recommendation tied to a detected signal?
3. Report visualized (Mermaid + table)?
4. Install commands real and verified?
5. No irrelevant padding?
