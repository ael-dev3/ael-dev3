# 🧙 Ael — Full-Stack & Game Engineer

**Specializing in real-time TypeScript systems, WebGL/Three.js, and onchain data pipelines.**

I design, implement, test, and ship browser-based products across interactive 3D, persistent multiplayer state, Farcaster identity, and reproducible blockchain analytics. I build persistent worlds and deterministic systems—the kind of engineering that should still work after the magic wears off.

**Links:** [Warpkeep](https://warpkeep.com/) · [Warpkeep on Farcaster](https://farcaster.xyz/~/channel/warpkeep)

## Selected projects

### [Warpkeep](https://github.com/ael-dev3/Warpkeep) — persistent multiplayer strategy world

[Live Alpha](https://warpkeep.com/) · React · TypeScript · Three.js/WebGL · SpacetimeDB · Cloudflare Workers · Farcaster

Built and shipped a browser and Farcaster Mini App strategy world with a server-authoritative, persistent realm. The live invite-only Alpha currently serves a founding cohort of **approximately eight admitted Farcaster players**, each returning to a durable keep with four asynchronous Workers. The system covers verified identity and admission, persistent ownership and resources, worker journeys, mobile/desktop rendering, additive database migrations, operational tooling, asset provenance, and release verification.

[![Warpkeep Genesis 001 realm](https://raw.githubusercontent.com/ael-dev3/Warpkeep/main/docs/reference/screenshots/2026-08-02-alpha-0.3.43-launch/warpkeep-alpha-0.3.43-genesis-001.png)](https://warpkeep.com/)

### [Degen Dogs Mission 3 Analytics](https://github.com/ael-dev3/Degen-Dogs-Mission-3) — reproducible Base analytics

[Live dashboard](https://ael-dev3.github.io/Degen-Dogs-Mission-3/) · Python · SQL/SQLite · Base/EVM · Vite · GitHub Pages

Built a reconstructable onchain analytics and archive pipeline that reads Base RPC and contract data, decodes it in Python, executes an approved SQLite query layer, and publishes inspectable CSV/JSON datasets and a static dashboard. The checked-in pipeline cross-verifies current state across providers, covers **200+ auctions**, unifies Mission 1–3 search, and includes automated consistency checks, refresh telemetry, recovery runbooks, and hourly publishing support.

### [Ashen Hallow](https://github.com/ael-dev3/Ashen-Hallow) — deterministic browser autobattler

[Play](https://ael-dev3.github.io/Ashen-Hallow/) · TypeScript · Canvas · Vite

Built a playable two-faction fantasy strategy game with **eight units and four building types**, grid deployment, persistent army progression, seeded enemy AI, pathfinding, touch controls, and data-driven combat mechanics. The engine separates domain, simulation, AI, rendering, input, and audio layers; releases are gated by production builds, deterministic gameplay regressions, and automated architecture contracts.

## Technical stack · spellbook

**Languages:** TypeScript, JavaScript, Python, SQL, HTML, CSS, GLSL  
**Frontend and graphics:** React, Three.js, WebGL, Canvas, responsive UI, Vite  
**Backends and data:** Node.js, Deno, SpacetimeDB, SQLite, Firebase/Firestore, Cloudflare Workers  
**Web3:** Farcaster SDK and Auth, Base/EVM, viem, JSON-RPC, contract calls, event indexing, DuneSQL  
**Quality and delivery:** Vitest, deterministic regression testing, architecture contracts, GitHub Actions, GitHub Pages, migration and recovery runbooks  
**Asset pipelines:** glTF/GLB, mesh optimization, runtime asset verification, provenance and licensing controls

## How I work

I run an AI-augmented engineering workflow using Codex and Hermes to increase research, implementation, and QA throughput. I remain accountable for architecture, implementation choices, code review, testing strategy, security boundaries, acceptance criteria, and release decisions.

I enjoy building systems that are deterministic where correctness matters, expressive where users feel them, and documented well enough to recover.

> Build the realm. Define the rules. Test the magic.
