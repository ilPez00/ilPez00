# The Physis lineage — one map

*Public-safe. Links point only at public artifacts. Updated 2026-11-21.*

**One idea:** declare the intended state, measure the real one, make the gap
visible, correct it — and keep replayable provenance from every claim back to
its evidence. A model is an interface, never the foundation.

The name "Physis" covers several public artifacts at different stages of that
idea. This is the canonical map:

| Artifact | What it is | Status | License / access |
|---|---|---|---|
| **[physis-computer](https://github.com/ilPez00/physis-computer)** | The current engine, as a free public release: typed world model of a codebase — observe, act, re-observe, verify. CLI + HUD + desktop GUI, fully offline. | **Active — start here.** v1.8.7 (2026-10-31), checksummed release archives. | Binaries redistributable with the package; corpus + docs Apache-2.0. Engine source is commercial. |
| **[physis-core](https://github.com/ilPez00/physis-core)** | The open research crate: embed, classify, cohere over a document corpus; hybrid retrieval under a token budget; provenance-bearing claims. CLI/HTTP/MCP/TUI. | **Published research lineage.** v0.1.25 on crates.io, 496 downloads (2026-11-21). Used by external researchers. | Apache-2.0, fully open. |
| **[physis-pro](https://github.com/ilPez00/physis-pro)** | The 2025 engine: ontological classification (70-cell semiotic grid), coherence tracking, predictive planning. | **Legacy, source-available.** Kept for reference and for pieces the current engine does not carry (voice binary, HTTP API). Still powers the [praxisweb.xyz/physis](https://praxisweb.xyz/physis) demo. | Source-available; see repo LICENSE (EULA — licensed, not sold). |
| **[physis-replant](https://github.com/ilPez00/physis-replant)** | Verified record→replay of tool recipes: stop paying an LLM to plan the same task twice. Measured 99% token reduction in a real n8n loop. | Active, experimental. | Apache-2.0. |
| **[physis-skill](https://github.com/ilPez00/physis-skill)** | Agent skill: verify a claim against running code before making it. Born from four compiled-but-never-called symbols. | Active. | See repo. |
| **[hermes-physis](https://github.com/ilPez00/hermes-physis)** | Evidence-backed execution memory for Hermes Agent; bundles both engines. | Active. | See repo. |
| **physis-next** | The active engine source behind physis-computer, and the commercial **Physis Context MCP** server for editors/agents. | **Private / licensed.** The public release above is the supported way to try it; licensing via the contact below. | Commercial (€49 founding / €79 after, per physis-computer README). |

**Rules of thumb for readers**

- Want to *try the current product* → physis-computer (or the
  [live workbench](https://praxisweb.xyz/physis/workbench), no install).
- Want *open source to build on* → physis-core (Apache-2.0 crate).
- Want *the 2025 ontology engine* → physis-pro (legacy, source-available).
- Archived `physis-*` machine repos (euclid, kairos, logos, …) are historical
  experiments, preserved immutable; they are not products.

Contact: [pezzingiovanniantonio@gmail.com](mailto:pezzingiovanniantonio@gmail.com) ·
[praxisweb.xyz/me](https://praxisweb.xyz/me)