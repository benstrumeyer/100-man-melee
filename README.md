# 100-Man Melee

A **free-for-all, last-fighter-standing brawl for ~100 fighters in one arena** — a browser-based platform fighter built in JavaScript, no plugins.

Spawn a horde of CPUs (and yourself) into a wide multi-tier arena and fight until one remains. Runs at 60 fps on a capable machine.

> **Built on [MeleeLight](https://github.com/schmooblidon/meleelight)** by Will Blackett (schmooblidon) — an open-source recreation of Super Smash Bros. Melee's movement and physics. This project extends that engine from its original 4-player cap to a ~100-fighter free-for-all. MeleeLight is MIT licensed; this project keeps that license (see [`LICENSE`](./LICENSE)) and is itself MIT.

## Play it locally

Requires Node 18+.

```bash
npm install
npm run dev          # Vite dev server, prints a localhost URL
```

Open the URL, wait for the title screen, then in the browser console (F12):

```js
startHundredManMatch(40)   // N fighters: you (port 0) + (N-1) CPUs. 40 is smooth; 100 is heavier.
```

You play port 0 on a GameCube controller (via adapter) or keyboard; the rest are CPUs. Last fighter standing wins.

## What's here (Phase 1 — local)

- **N-fighter engine** — the original 4-player cap removed throughout (game loop, rendering, AI, per-fighter state).
- **FFA last-man-standing** with real eliminations.
- **Wide multi-tier arena** — a big flat platform plus Battlefield-height pass-through platforms.
- **Broad-phase collision** (spatial hash) + fps/sim instrumentation; the sim stays ~3 ms/tick at 100 fighters.
- **Fixed full-arena camera** framing the whole stage.

## Roadmap (Phase 2 — online)

The local simulation is designed to become an **authoritative server** so ~100 *humans* can play in one arena: clients send inputs, the server runs the one true sim and broadcasts state, with client-side prediction. Real Melee netplay caps at 4 players — an open JS engine is the way around that.

## Tech

JavaScript · Vite · Vitest · HTML5 Canvas. Migrated from the original Webpack 1 / Babel 6 toolchain.

## Credits & license

- Engine base: **[MeleeLight](https://github.com/schmooblidon/meleelight)** — © Will Blackett, MIT.
- 100-man fork & extensions: this repository, MIT.

MIT — see [`LICENSE`](./LICENSE).
