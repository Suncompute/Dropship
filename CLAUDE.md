# CLAUDE.md — Dropship

## Projekt
A fast-paced 2D space shooter where you pilot a tactical Dropship through the void, hunting hostile planets before they awaken. Rendered in a silky shadow-style aesthetic, the game blends minimalism with cosmic brutality. Every world you face is a living target — rotating, shielding, mutating — and your mission is simple: strike first or be erased. Powered by WebAssembly, the game runs instantly in the browser, offering smooth online play, tight controls, and a dark, atmospheric universe that feels hand-carved from shadow.

## Architektur: hexagonal

### Crates
- **`dropship-core`** L1 — Domain Entities, Game Logic, Business Rules
- **`dropship-ports`** L2 — Port Traits (Renderer, Input, Audio, ...)
- **`dropship-wasm`** L3 — WASM Entry-Point, WebGL Adapter, Browser Glue

## Hard Rules
- Dependencies immer **inward**: L3 → L1. Niemals umgekehrt.
- `cargo check -p <crate>` vor jedem Commit.
- Kein `.unwrap()` in Production-Code — immer `Result`/`Option` propagieren.
- Kein `panic!()` außer in Tests.
