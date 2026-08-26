# gio

**I like to fix things. Time around me seems to move faster, for some reason.**

Twenty-seven, in Verona. I build software and I run the machines it runs on.

---

### The machine room

Two computers in a house in Verona serve [praxisweb.xyz](https://praxisweb.xyz), hold its
database, take live card payments and replicate to each other.

| Host | Role | What it carries |
|---|---|---|
| **pansa** | Primary | Application, self-hosted Postgres, tunnel connector |
| **air** | Warm standby | Streaming database replica, second tunnel connector |

No cloud provider is involved. When something breaks at three in the morning, the person
who fixes it is me.

---

### What I run

**[Praxis](https://praxisweb.xyz)** — a goal journal and accountability tool. Daily brief in
the morning, one-tap check-in, recap at night, and a way for people working towards the same
thing to verify each other's work. Installable, and it keeps working with no network.

`TypeScript` · `React` · `Express` · `Postgres` · `Stripe` · `Offline PWA` · `Android`

---

### Also built

| Project | Language | |
|---|---|---|
| [physis-core](https://github.com/ilPez00/physis-core) | Rust | Embedding, classification and coherence engine. Apache 2.0. |
| [cyclops-wearable](https://github.com/ilPez00/cyclops-wearable) | Python | Open wearable AI note-taker — XIAO S3 and Arduino HUD firmware, local-first brain, Android companion. |
| [pika-hermes](https://github.com/ilPez00/pika-hermes) | Kotlin | Android phone agent running any GGUF model offline, with a 40-provider cloud cascade behind it. |
| [agent-bridge](https://github.com/ilPez00/agent-bridge) | Python | Crash-safe shared session ledger for multi-agent setups — dead agents still report. |

Forty-five public repositories since 2022, in TypeScript, Rust, Kotlin and Python.

---

### Available for work

I take contract work alongside Praxis. I am most useful where one person needs to own a
system end to end — from the database to the deploy — rather than fill one seat on a large
team.

- Full-stack TypeScript — React, Express, Postgres
- Self-hosting and migration off platform bills
- Offline-capable PWAs and Android shells
- LLM plumbing — routing, fallback, cost control

**[praxisweb.xyz/me](https://praxisweb.xyz/me)** · [pezzingiovanniantonio@gmail.com](mailto:pezzingiovanniantonio@gmail.com)

Tell me what is broken or what you want built. I answer within a day, and I will say so
plainly if it is not something I should take.
