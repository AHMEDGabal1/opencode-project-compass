# project-compass catalog

Curated map of project signals → recommended tooling. This is the **base** layer;
combine with a live WebFetch when the user wants "what's new" or a niche is thin.
Mark every item `known` (from this catalog). Any item added from a live lookup is
marked `as of <date>` and must cite its source URL.

Priority: `must` = blocks safe work · `nice` = speeds it up · `watch` = emerging, optional.

---

## Languages

| Signal | Skills | Plugins | MCP | External AI tools | Priority |
|--------|--------|---------|-----|-------------------|----------|
| TypeScript / JavaScript (package.json) | front-review, front-refactor, front-comments, test-guard, clean-code-guard | — | filesystem, git, github | v0, Cursor, GitHub Copilot | must |
| Python (pyproject.toml / requirements.txt) | clean-code-guard, test-guard, pr-prep | — | filesystem, git, github | Jupyter AI, Continue, Codium | must |
| Go (go.mod) | clean-code-guard, pr-prep | — | filesystem, git, github | — | must |
| Rust (Cargo.toml) | clean-code-guard | — | filesystem, git, github | rust-analyzer + LLM | nice |
| PHP (composer.json) | wp-guard, woo-guard (if WP/Woo), clean-code-guard | — | filesystem, git, github | — | must (WP/Woo) |
| Ruby (Gemfile) | clean-code-guard | — | filesystem, git, github | — | must |
| Java / C# (pom.xml / build.gradle / *.csproj) | clean-code-guard, pr-prep | — | filesystem, git, github | JetBrains AI | must |
| Elixir (mix.exs) | clean-code-guard | — | filesystem, git, github | — | nice |

---

## Frameworks

| Signal | Skills | Plugins | MCP | External AI tools | Priority |
|--------|--------|---------|-----|-------------------|----------|
| React / Vue / Svelte / Astro / Next | front-a11y, front-review, front-refactor, front-comments | — | Playwright/Puppeteer (e2e) | v0, Locofy | must (a11y) |
| Django / Flask / FastAPI | clean-code-guard, test-guard | — | Postgres/sqlite (if DB) | — | must |
| Laravel | wp-guard (patterns), clean-code-guard | — | filesystem, git | — | nice |
| WordPress (wp-content) | wp-guard | — | filesystem, git | — | must |
| WooCommerce | woo-guard | — | filesystem, git | — | must |
| Supabase (dep or .supabase) | supabase, supabase-postgres-best-practices, opencode-supabase-guide | — | supabase | — | must |
| Spring / Express / Nest | clean-code-guard, test-guard | — | Postgres/sqlite | — | must |

---

## Domains / Infra

| Signal | Skills | Plugins | MCP | External AI tools | Priority |
|--------|--------|---------|-----|-------------------|----------|
| ML / Data (torch, tensorflow, notebooks) | clean-code-guard | — | filesystem, sqlite | NotebookLM, Hugging Face, PyTorch AI | nice |
| Docker (docker-compose.yml) | pr-prep | docker | filesystem, git | — | nice |
| Kubernetes (*.yaml + k8s) | clean-code-guard | k8s | kubernetes | — | nice |
| Terraform / IaC (*.tf) | clean-code-guard | — | terraform | — | nice |
| CI present (.github/workflows, .gitlab-ci) | pr-prep | — | github | — | nice |

---

## Always-on baseline (almost every project)

| Tool | Type | Why | Priority | Command |
|------|------|-----|----------|---------|
| git MCP | MCP | repo history, diffs, blame | must | `opencode mcp add git` |
| filesystem MCP | MCP | read/write within project | must | `opencode mcp add filesystem -- <root>` |
| github MCP | MCP | PRs, issues, CI status | nice | `opencode mcp add github` |
| clean-code-guard skill | skill | pre-ship code review | must | copy SKILL.md |
| pr-prep skill | skill | commit/PR write-up | nice | copy SKILL.md |

---

## Live-trend watchlist (WebFetch seeds)

Run when the user asks for freshness or a niche above is empty:
- `"<stack> best AI coding tools 2026"`
- `"new Model Context Protocol servers <stack>"`
- `"agent skills for <framework> developers"`
- `"AI dev tool launches this month"`

Only fold in results that are named, current, and from a credible source.
Cite the URL next to each live item.
