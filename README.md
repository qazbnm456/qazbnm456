### Hi, I'm Syue Siang Su (Boik Su) 👋

Security Research Manager at [CyCraft Technology](https://www.cycraft.com/), based in Taiwan. I maintain
[**awesome-web-security**](https://github.com/qazbnm456/awesome-web-security) — a curated web-security
learning list, 13.6k★ / 1,800+ forks — and lately I've been building infrastructure for LLM agents that
have to get security judgment *right*, not just look plausible.

---

### What I'm building right now

Four agents, each pointed at a real problem instead of a benchmark. Two of them are things you can
install and use today:

**[diff-sentry](https://github.com/qazbnm456/diff-sentry) — catch a malicious pull request before you
merge it.** A GitHub Action that reads a change the way an attacker hopes you won't: `pull_request_target`
that checks out the PR head, base64 that decodes to a shell payload, secrets reaching a network sink,
payloads shoved past the diff viewport by a whitespace run. Fifteen lines of YAML, and no API key, no
model and no network — so it runs on fork pull requests under the read-only token they already get.

```yaml
- uses: qazbnm456/diff-sentry@v0.4.0
```

**[ctx-distillery](https://github.com/qazbnm456/ctx-distillery) — your coding agent's memory rots.
Distil it.** Every project you work on with an AI coding agent accumulates a pile of past conversations
too large to read and a memory store that quietly starts contradicting the code. This reads both and
proposes what to prune and what is worth promoting into a durable memory file or a reusable Skill — and
never writes a byte without your explicit, per-candidate approval. Ships as a PyPI package and as an
Agent Skill.

```bash
uv tool install "ctx-distillery[cli]"
npx skills add qazbnm456/ctx-distillery
```

Two more are research agents rather than products, and honest about it:

| Project | What it does |
|---|---|
| **[cve-reverser](https://github.com/qazbnm456/cve-reverser)** | Reverses a *publicly disclosed* WordPress CVE from its patch into a local-lab PoC and a Nuclei detection template. Strict planner/lifeline/generator role separation, so no single model both reasons about the bug and writes the final template unchecked. |
| **[toolscout](https://github.com/qazbnm456/toolscout)** | Implements Microsoft's ATLAS method: a small planner solves tasks over a huge MCP toolspace by discovering it progressively (list → load → describe → call) instead of holding hundreds of tool schemas in context. |

All four sit on **[rlm-harness](https://github.com/qazbnm456/rlm-harness)** — a reusable harness over
[DSPy](https://dspy.ai)'s Recursive Language Model module. Every task gets a full, replayable JSONL trace
(main steps, sub-model calls, tool calls), execution is sandboxed by default (pyodide/Deno; raw local
execution is refused unless you opt in), and those traces export as reward-free SFT/RL datasets. It is
domain-agnostic — security just happens to be my own first use of it.

The through-line: every verdict traces back to evidence rather than being trusted as self-report, every
run is exportable as training data, and every README says plainly what is *not* solved yet. I would
rather ship an honest residual-risk section than a demo that only works once.

---

### Elsewhere

[Blog / writing](https://www.boik.tw/) · [X (formerly Twitter)](https://x.com/boik_su) · [Patreon](https://www.patreon.com/boik)
