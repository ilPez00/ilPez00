# gio

**I build self-healing systems with as little AI as the job allows.**

**[Hire me](#available-for-work)** · **[Explore the software](#the-three-systems)** · **[Research](#research-measured-not-asserted)**

Twenty-seven, in Verona. Three systems — in Rust, TypeScript and Python — on a mesh of machines
I own and operate. One of the three generates that mesh and runs it: plug a machine in and it
configures itself. The pattern is always the same: declare the intended state, measure the real
one, make the gap visible, correct it. Every layer that can be deterministic
is deterministic. A model gets called only where nothing cheaper works, and it is an
interface, never the foundation.

---

### The machine room

Two computers in a house in Verona serve [praxisweb.xyz](https://praxisweb.xyz), hold its
database, take live card payments and replicate to each other.

| Host | Role | What it carries |
|---|---|---|
| **pansa** | Primary | Application, self-hosted Postgres, tunnel connector |
| **air** | Warm standby | Streaming database replica, second tunnel connector |

No cloud provider is involved. When something breaks at three in the morning, the person who
fixes it is me.

---

### The three systems

**[Praxis](https://praxisweb.xyz)** — a goal journal and accountability platform.
Live with **45 users, 3 on paid plans**. A clinical psychologist runs it with a group of
socially withdrawn young adults: shared task delegation and peer verification turn daily
self-care routines into commitments someone else can see and confirm. Daily brief in the
morning, one-tap check-in, recap at night. Installable, and it keeps working with no network —
client state is written offline first and reconciled deterministically, so the same edit
sequence converges to the same state on every device. Android shipped through **3.7.0** in
**7 languages**, plus SwiftUI iOS, an Electron desktop build, and an MCP server that exposes
the journal to agents. *Logged reality, not intention, is what revises the plan.*
→ [Production case study](https://github.com/ilPez00/praxis-case-study)

`TypeScript` · `React 19` · `Express 5` · `Supabase/Postgres` · `Stripe` · `Offline PWA` · `Android` · `SwiftUI`

**[physis-computer](https://github.com/ilPez00/physis-computer)** — the current Physis engine
as a free, fully offline release: a typed world model of your codebase. Observe, act,
re-observe, verify — every answer cites the primitive it came from, and the machine abstains
rather than guesses. CLI, HUD and desktop GUI; Linux and Windows; checksummed release
archives, reversible install, no account and no network. Try it without installing: the
[live workbench](https://praxisweb.xyz/physis/workbench) runs the same observe pass over an
uploaded repository. **Verified 2026-11-21 on a fresh download:** every SHA-256 matches, the
7-stage demo passes its checks, and the binary answers correctly inside an empty network
namespace — offline is a measured property, not a slogan. Free binaries + Apache-2.0 corpus;
the engine source is the commercial product.

`Rust` · `Offline` · `MCP` · `v1.8.7`

**[aion](https://github.com/ilPez00/aion)** — the mesh. Not a controller sitting beside one:
aion generates the mesh and runs it. RandoMesh is that mesh written down — documentation,
not a second codebase.

Plug a machine in and it configures itself. aion provisions the control plane over SSH with
idempotent installers, systemd units and timers (*disable* is deliberately not *uninstall*),
then owns the lifecycle of everything running there — Praxis, physis, llama-server inference
nodes, gateways. Topology is emitted into the fleet config and read back on every probe, so
operator intent beats built-in defaults and drift shows up as a diff instead of a stale HUD.
Zero registry by design: an instance's name derives its port, discovery is a file heartbeat,
and there is nothing to register a new node with. Cross-node transport is an SSH tunnel
rather than a hand-rolled TLS/PKI stack. One cockpit probes every service on every node and
drives it; one `Intent` type for every input device — keyboard, gamepad, voice, a custom
hardware deck. **2,195 tests pass on a fresh checkout** (2026-11-21; the fleet e2e module
needs two live machines). *A dead node is a state, not an outage: the mesh reports it
and routes around it.*

`Python` · `asyncio` · `SSH` · `systemd` · `Apache-2.0`

---

### The Physis lineage — one map

The name covers several public artifacts at different stages of one idea. Canonical map
(full version: [PHYSIS-MAP.md](PHYSIS-MAP.md)):

| Artifact | What it is | Status |
|---|---|---|
| [physis-computer](https://github.com/ilPez00/physis-computer) | Current engine, free public release | **Active — start here** |
| [physis-core](https://github.com/ilPez00/physis-core) | Open research crate (Apache-2.0, crates.io) | Published research lineage |
| [physis-pro](https://github.com/ilPez00/physis-pro) | 2025 ontology engine | Legacy, source-available; still powers the [/physis demo](https://praxisweb.xyz/physis) |
| [physis-replant](https://github.com/ilPez00/physis-replant) · [physis-skill](https://github.com/ilPez00/physis-skill) · [hermes-physis](https://github.com/ilPez00/hermes-physis) | Verified replay · claim-checking skill · Hermes integration | Active |
| physis-next + Physis Context MCP | Active engine source + commercial editor/agent server | Private / licensed — [contact](mailto:pezzingiovanniantonio@gmail.com) |

Archived `physis-*` machine repos are historical experiments, preserved immutable.

---

### Research — measured, not asserted

**[physis-core](https://github.com/ilPez00/physis-core)** — a Rust engine that reduces a
corpus to structure: what repeats, what differs, what contradicts. Competing hypotheses stay
side by side instead of collapsing early, and every claim carries replayable provenance back
to its evidence. Hybrid BM25 + cosine retrieval under a fixed token budget; fully offline.
**496 downloads on crates.io** (839 across both crates, 2026-11-21), used autonomously by
researchers outside the project: in optimization, for the predrafter and checker; in
alignment, for neurosemantic orchestration and context compilation. Semantic retrieval
**hit@5 0.57 vs 0.14** lexical baseline; proposal ranking **top-3 0.712 vs 0.136**
permuted-label null — published as triage, explicitly *not* certification. Negative results
stay in the record: filing-certification scored at chance and is published as a NO.
*A measured failure rewrites the structure that produced it.*

**[physis-psychopomp](https://github.com/ilPez00/physis-psychopomp)** — possible worlds made
experimentally accountable: provenance-bearing world states, temporal reasoning, falsifiable
constraints. Pre-registered claims and failure criteria; a first public audit found two
experimental blockers (a vacuous control, a non-identifiable target) — both confirmed in code
and fixed. **75 tests pass** on a fresh checkout (2026-11-21). A prior JEPA-derived latent in
this lineage was falsified at scale and the shuffled-label control exists because of it.
No claim is asserted ahead of its evidence.

**[epistemics-sprint](https://github.com/ilPez00/epistemics-sprint)** — *Absence is not
refutation.* An evidence-state benchmark (26 cases, 71 claims) separating "the records
contradict this" from "the records are silent" — most benchmarks score both as false,
rewarding confident guessing. Raw outputs, scorer and report published; the scorer
reproduces the published tables offline (re-verified 2026-11-21).

---

### Also built

| Project | Language | |
|---|---|---|
| [physis-replant](https://github.com/ilPez00/physis-replant) | Rust | Stop paying an LLM to plan the same task twice. **Measured in a real n8n loop: 99% fewer tokens** (45,200 → 452 over 100 iterations), both arms executing 100 real actions + 100 independent checks. 25 tests green on fresh checkout. |
| [agent-bridge](https://github.com/ilPez00/agent-bridge) | Python | Crash-safe shared session ledger for multi-agent setups — dead agents still report, read post-mortem from each harness's native store. |
| [tracker-libraries](https://github.com/ilPez00/tracker-libraries) | TypeScript | **2,439 records across 25 datasets**, zero runtime dependencies — the autocomplete half of every tracking app, extracted from Praxis and released standalone. MIT. |
| [physis-skill](https://github.com/ilPez00/physis-skill) | Shell | An agent skill that makes an assistant verify a claim against running code — built after four declared-and-exported symbols turned out to be called by nothing. |
| [cyclops-wearable](https://github.com/ilPez00/cyclops-wearable) | Python/C++ | Open wearable AI note-taker — XIAO S3 + Arduino HUD firmware, local-first brain, Android companion. Zero-dep test suite + end-to-end demo pass without hardware. |
| [pika-hermes](https://github.com/ilPez00/pika-hermes) | Kotlin | Android phone agent running any GGUF model offline, with a 40-provider cloud cascade behind it. Built on a fork — the local execution and provider fallback are mine, the codebase is not. |
| kOS / KSP | Kerboscript | Autonomous GNC scripting on top of the open-source kOS environment — UPFG/PEG-inspired guidance, state-driven orbital maneuvers. |

Sixty-seven public repositories since 2022, in TypeScript, Rust, Kotlin and Python.
Forks carry their upstream attribution; archived repos say what superseded them.

---

### Before software

CAD designer for industrial food-processing machinery, then two years selling custom
3D-printed parts in engineering-grade materials — CAD to material choice to finishing to
delivery. ITS Meccatronico: PLC logic, device control, low-level C on 8-bit PIC
microcontrollers. Philosophy at Verona, in progress — symbolic logic, semantics, ontology.
Hardware is never the ideal on paper, and neither is a deadline.

---

### Available for work

I take contract work alongside Praxis. I am most useful where one person needs to own a
system end to end — from the database to the deploy — rather than fill one seat on a large
team. Two fixed-scope offers:

1. **Systems audit & self-hosting migration** — one week, fixed scope: a written map of what
   you run, its failure modes, its real cost, and a migration plan off platform bills onto
   hardware you own. Deliverable: report + runbook, presented live. Quote on request.
2. **Offline-first product build** — fixed milestones from spec to deploy: an offline-capable
   PWA or Android shell with deterministic sync, on infrastructure you own. Deliverable:
   working software + the tests that prove it. Quote on request.

Also: full-stack TypeScript (React, Express, Postgres), LLM plumbing (routing, fallback,
cost control, retrieval that is measured rather than assumed), reliable agent integrations.

**[praxisweb.xyz/me](https://praxisweb.xyz/me)** · [pezzingiovanniantonio@gmail.com](mailto:pezzingiovanniantonio@gmail.com)
English C2 (Cambridge CAE) · Italian native

Tell me what is broken or what you want built. I answer within a day, and I will say so
plainly if it is not something I should take.