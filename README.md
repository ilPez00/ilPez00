# gio

**I build self-healing systems with as little AI as the job allows.**

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

`TypeScript` · `React 19` · `Express 5` · `Supabase/Postgres` · `Stripe` · `Offline PWA` · `Android` · `SwiftUI`

**[physis-core](https://github.com/ilPez00/physis-core)** — a Rust engine that reduces a
corpus to structure: what repeats, what differs, what contradicts. Competing hypotheses stay
side by side instead of collapsing early, and every claim carries replayable provenance back
to its evidence, so a wrong answer is traceable rather than mysterious. Hybrid BM25 + cosine
retrieval under a fixed token budget; embedder, n-gram table and tokenizer are swappable
interfaces; runs fully offline. One engine, four surfaces — CLI, HTTP server, MCP server, TUI.

**410 downloads on crates.io** (721 across both crates), used autonomously by researchers
outside the project: in optimization, for the predrafter and checker; in alignment, for
neurosemantic orchestration and context compilation, where the model stays conceptually
sandboxed and the structure around it stays inspectable.

Measured rather than asserted: semantic retrieval **hit@5 0.57 vs 0.14** lexical baseline;
proposal ranking **top-3 0.712 vs 0.136** permuted-label null — published as triage, explicitly
*not* certification. Negative results stay in the record. *A measured failure rewrites the
structure that produced it.*

`Rust` · `Apache-2.0` · `ONNX` · `MCP`

**[aion](https://github.com/ilPez00/aion)** — the mesh. Not a controller sitting beside one:
aion generates the mesh and runs it. RandoMesh is that mesh written down — documentation,
not a second codebase.

Plug a machine in and it configures itself. aion provisions the control plane over SSH with
idempotent installers, systemd units and timers (*disable* is deliberately not *uninstall*),
then owns the lifecycle of everything running there — Praxis, physis, llama-server inference
nodes, gateways. Topology is emitted into the fleet config and read back on every probe, so
operator intent beats built-in defaults and drift shows up as a diff instead of a stale HUD.
Zero registry by design: an instance's name derives its port, discovery is a file heartbeat,
and there is nothing to register a new node with — no daemon, no mDNS, no port scan. Cross-node
transport is an SSH tunnel rather than a hand-rolled TLS/PKI stack: encryption, host
authentication and per-peer keys for no new protocol code.

One cockpit probes every service on every node — TCP, HTTP health or systemd — and drives it.
One `Intent` type for every input device: keyboard, gamepad, voice, a custom hardware deck.
Every backend a swappable harness. *A dead node is a state, not an outage: the mesh reports it
and routes around it.*

`Python` · `asyncio` · `SSH` · `systemd`

---

### Also built

| Project | Language | |
|---|---|---|
| [physis-skill](https://github.com/ilPez00/physis-skill) | Shell | An agent skill that makes an assistant verify a claim against running code — built after four declared-and-exported symbols turned out to be called by nothing. |
| [cyclops-wearable](https://github.com/ilPez00/cyclops-wearable) | Python | Open wearable AI note-taker — XIAO S3 and Arduino HUD firmware, local-first brain, Android companion. |
| [pika-hermes](https://github.com/ilPez00/pika-hermes) | Kotlin | Android phone agent running any GGUF model offline, with a 40-provider cloud cascade behind it. Built on a fork — the local execution and provider fallback are mine, the codebase is not. |
| kOS / KSP | Kerboscript | Autonomous GNC scripting on top of the open-source kOS environment — UPFG/PEG-inspired guidance, state-driven orbital maneuvers. |

Forty-five public repositories since 2022, in TypeScript, Rust, Kotlin and Python.

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
team.

- Full-stack TypeScript — React, Express, Postgres
- Self-hosting, multi-node operation, migration off platform bills
- Offline-capable PWAs and Android shells
- LLM plumbing — routing, fallback, cost control, retrieval that is measured rather than assumed

**[praxisweb.xyz/me](https://praxisweb.xyz/me)** · [pezzingiovanniantonio@gmail.com](mailto:pezzingiovanniantonio@gmail.com)
English C2 (Cambridge CAE) · Italian native

Tell me what is broken or what you want built. I answer within a day, and I will say so
plainly if it is not something I should take.
