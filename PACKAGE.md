# PACKAGE.md — Repository conventions

## Layout

Discipline-first monorepo: `products/` (per-line specs) · `mechanical/` · `electronics/` · `firmware/` · `certification/` · `manufacturing/` · `supply-chain/` · `validation/` · `packaging/` · `test-tools/` · `business/` · `legal/` · `docs/` · `rfcs/` · `labs/` · `sandbox/` · `tooling/` · `security/`.

Root `README.md` has the rules of thumb; every folder's `purpose.txt` is normative for what it may contain.

## Placement rules (normative)

| From | Rule |
|---|---|
| `products/<line>/` | Specs, requirements, variants, release records + **links** to artifacts. Never copies of CAD/gerbers/firmware binaries. |
| `mechanical/`, `electronics/`, `firmware/` | The single source of truth for its discipline. Firmware shared across lines lives here; line config is referenced from `firmware/boards/` + `products/<line>/release/`. |
| `validation/` | Every physical test: plan → sample → report. Certification evidence stays in `certification/`; validation informs it. |
| `manufacturing/test-jigs` vs `test-tools/` | Fixture *documents* (drawings, procedures) in `manufacturing/`; fixture *software* in `test-tools/`. |
| `packaging/inserts` vs `content/` | Print-ready layout in `packaging/`; the written copy in `content/`. |
| Generated outputs | Only produced by `tooling/exporters/` — never hand-edited; regenerated on change of source. |
| `sandbox/`, `labs/` | Experimental; promotion to production folders is an explicit reviewed move, never implicit. |
| `business/`, `legal/`, `docs/` | Humans/agents only — never referenced as inputs by build/test scripts. |

## Release discipline

Each `products/<line>/release/<rev>/` pins the exact versions shipped: PCB revision, firmware tag, BOM revision, tooling revisions, certification report ids. If it shipped, the release record names every artifact version.

## Process

- **Decisions:** RFC (`rfcs/`) → discussion → ADR (`docs/decisions/` from `TEMPLATE.md`); ADRs are append-only for amendments.
- **BOM integrity:** `supply-chain/bom/master-bom.csv` is machine-checked in CI (required fields, lifecycle flags, alternates).
- **Data:** any curated dataset needs a schema in `datasets/schemas/` (full-stack variant).
