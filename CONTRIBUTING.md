# Contributing

Thanks for helping build this product.

## Ground rules

1. **Read `PACKAGE.md`** — placement rules are normative; `purpose.txt` in every folder says what belongs there.
2. **Every new folder ships with a `purpose.txt`** (`PURPOSE:` / `SHOULD CONTAIN:` / `SEE:`).
3. **No empty scaffolding** — create folders when the work arrives.
4. **Engineering choices go through process:** RFC in `rfcs/` → discussion → ADR from `docs/decisions/TEMPLATE.md`.
5. **Compliance claims need evidence** — link the standard number or lab report; never state a certification status without a document in `certification/`.
6. **Generated files are regenerated**, never edited (Gerbers, STEP/STL, PDF exports).

## Workflow

```bash
# firmware
make build          # or the board-specific build (see firmware/boards/<board>/)
make test

# repo hygiene
pnpm lint           # purpose.txt presence, BOM lint, link check (once configured)
```

## Pull requests

- One concern per PR; a release-affecting change updates `products/<line>/release/` too
- Quality defects reference a `manufacturing/quality/ncr/` record
- Keep `labs/` and `sandbox/` clearly separated from production folders

## Commit style

Conventional commits with a discipline scope: `feat(firmware):`, `fix(electronics):`, `docs(certification):`, `chore(supply-chain):`.
