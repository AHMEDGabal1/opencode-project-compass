# project-compass report template

Render every analysis in this shape. Keep it scannable; the diagram leads, the
table backs it up, the score tells the user how far they are from "tooled up".

---

## 1. Detected profile

`{language} + {framework} + {domain} + {testing}`
*(one line, built only from files actually found)*

---

## 2. Tooling map (Mermaid)

```mermaid
graph TD
  P[Project: {name}] --> S[{detected profile}]
  S --> SK[Skills]
  S --> PL[Plugins]
  S --> MC[MCP servers]
  S --> EX[External AI tools]
  SK --> SK1[{skill}]
  SK --> SK2[{skill}]
  PL --> PL1[{plugin}]
  MC --> MC1[{mcp}]
  EX --> EX1[{tool}]
```

---

## 3. Recommendations

| Tool | Type | Why it fits | Priority | Install / enable |
|------|------|-------------|----------|------------------|
| {name} | skill / plugin / mcp / tool | {tied to detected signal} | must / nice / watch | `command` or "copy SKILL.md" |
| ... | | | | |

- Priority legend: **must** = blocks safe work · **nice** = speeds it up · **watch** = emerging/optional.
- Live items: append `as of <date>` and the source URL. Unverified items: label `unverified`.

---

## 4. Readiness score

`{score}/100` — {one line on what's missing or why full marks}.

Gaps:
- {missing must-have and its impact}
- {missing nice-to-have}

---

## 5. Skipped / not recommended

| Tool | Why skipped |
|------|-------------|
| {tool} | {YAGNI / doesn't fit detected stack} |
