### Hi, I'm Syue Siang Su (Boik Su) 👋

Security Research Manager at [CyCraft Technology](https://www.cycraft.com/), based in Taiwan. I maintain
[**awesome-web-security**](https://github.com/qazbnm456/awesome-web-security) — a curated web-security
learning list, 13.6k★ / 1,800+ forks — and lately I've been building infrastructure for LLM agents that
have to get security judgment *right*, not just look plausible.

---

### What I'm building right now

A small stack of tools on top of [DSPy](https://dspy.ai)'s Recursive Language Model module, going from
general-purpose harness down to real, adversarial security tasks:

**[rlm-kit](https://github.com/qazbnm456/rlm-kit)** — the foundation. A reusable harness over `dspy.RLM`:
every task gets a full, replayable JSONL trace (main steps, sub-model calls, tool calls), sandboxed
execution by default (pyodide/Deno; raw local execution is refused unless you opt in), and traces export
as reward-free SFT/RL datasets. Domain-agnostic — security just happens to be my own first use of it.

Three consumers built on it, each aimed at a real problem instead of a benchmark:

| Project | What it does |
|---|---|
| **[cve-reverser](https://github.com/qazbnm456/cve-reverser)** | Reverses a *publicly disclosed* WordPress CVE from its patch into a local-lab PoC and a Nuclei detection template — a traced, trainable agent, not a one-shot script. Strict planner/lifeline/generator role separation so no single model both reasons and writes the final template unchecked. |
| **[diff-sentry](https://github.com/qazbnm456/diff-sentry)** | Reproduces the shape of Datadog's BewAIre defense: classifies a GitHub diff as benign/suspicious/malicious, treating the diff as *untrusted data* inside a sandboxed REPL, never as instructions. Tested against a reconstruction of the actual `hackerbot-claw` incident payloads. |
| **[toolscout](https://github.com/qazbnm456/toolscout)** | Implements Microsoft's ATLAS method: a small planner solves tasks over a huge MCP toolspace by discovering it progressively (list → load → describe → call) instead of holding hundreds of tool schemas in context. |

The through-line across all three: every verdict is traced back to evidence rather than trusted as
self-report, every run is exportable as training data, and every README says plainly what's *not* solved
yet. I'd rather ship an honest residual-risk section than a demo that only works once.

---

### Elsewhere

[Blog / writing](https://www.boik.tw/) · [X (formerly Twitter)](https://x.com/boik_su) · [Patreon](https://www.patreon.com/boik)
