# ADR-0001: Discipline-First Structure for a Consumer-Hardware Monorepo

**Status:** Accepted
**Date:** 2026-10-30
**Deciders:** Template author
**Related:** `PACKAGE.md`, root `README.md`

---

## Context

Consumer-hardware development produces many artifact kinds — CAD, schematics, firmware, test reports, certifications, BOMs, packaging dielines, factory documents — that must stay in sync across revisions of multiple product lines. Common failure modes this structure must prevent:

1. **Artifact drift** — the same BOM or drawing exists in three folders; nobody knows which shipped.
2. **Release ambiguity** — after MP, nobody can reconstruct which PCB rev + firmware tag + tooling revision went into a batch.
3. **Compliance surprises** — certification evidence scattered across drives, discovered missing at lab time.
4. **Concurrent disciplines stepping on each other** — firmware and mechanical teams editing "the product folder" simultaneously.

## Decision

Organize by **engineering discipline** (`mechanical/`, `electronics/`, `firmware/`, `certification/`, `manufacturing/`, `supply-chain/`, `validation/`, `packaging/`, `test-tools/`), with `products/<line>/` holding only **specs, variants, and release records that link** to artifacts in discipline folders.

Supporting rules:

- **One source of truth per artifact kind.** Discipline folders own their artifacts; product folders reference them.
- **Release records pin versions.** `products/<line>/release/<rev>/` names PCB revision, firmware tag, BOM revision, tooling revisions, and certification report ids for everything that shipped.
- **Generated outputs are regenerated, never edited** — exports come from `tooling/exporters/` (STEP/STL/Gerber/PDF).
- **Validation ≠ certification.** `validation/` is internal reliability/behavioral testing (the analog of software tests); `certification/` holds regulatory evidence for labs and authorities.
- **Every folder carries a `purpose.txt`** (PURPOSE / SHOULD CONTAIN / SEE) so humans and AI agents place files consistently.
- **Decisions are recorded:** RFC in `rfcs/` for pending choices → ADR in `docs/decisions/` when landed.

## Consequences

### Positive
- A release record reconstructs a shipped batch completely.
- Discipline owners have clear territory → fewer merge conflicts and clearer `CODEOWNERS`.
- Certification readiness is visible as folders fill, not discovered at lab time.
- `purpose.txt` makes the repo self-describing for onboarding humans and AI agents.

### Negative & mitigations
| Cost | Mitigation |
|---|---|
| Cross-discipline features (e.g., a button: mechanical + electronics + firmware) span folders | `products/<line>/product.md` links all three; release records pin versions |
| Discipline-only view can hide the product | `products/` is the product view; README rules of thumb route contributors |
| Newcomers may deposit artifacts in the product folder | `PACKAGE.md` placement rules + lint for `purpose.txt` presence |

### Neutral
- No build system is assumed; add CI in `.github/workflows/` per discipline as tooling lands.

## Alternatives considered

1. **Product-folder-first** (everything for a line under `products/<line>/`) — rejected: shared firmware, common components, and single BOM truth duplicate across lines; discipline depth (test rigs, lab reports) doesn't fit.
2. **Flat shared drive with naming conventions** — rejected: exactly the drift and release ambiguity this ADR exists to prevent.
3. **PLM/PDM tool as the only system of record** — rejected for a template: tools like OpenBOM/KiCad PLM can be added later; the repo must remain meaningful without them.

## Compliance

- CI (`.github/workflows/`) enforces: `purpose.txt` presence, BOM field completeness, docs link integrity.
- Release PRs must update the matching `products/<line>/release/` record.
- Revisit at first mass-production partner selection (factory-facing structure may extend `manufacturing/`).

---

*Amendments: append below, dated — never rewrite the original text.*
