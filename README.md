# Arc docs site

Mintlify documentation site for [Arc](https://github.com/el-uno/fintech_arc) — a simulation of
cross-border stablecoin and fiat infrastructure for the EU↔Africa corridor.

Four tabs, 39 pages. The code Arc documents lives in a separate repository; this one holds only
the site.

| Tab | Covers |
| --- | --- |
| **Guide** | Orientation, quickstart, and the stablecoin/corridor primer with cited research |
| **Architecture** | The six contexts, ledger, chain layer, saga, compliance, testing, flows, ADRs |
| **Stories** | Seven engineering narratives — symptom → diagnosis → the mechanism that prevents it |
| **Practice** | Four interview question banks with worked answers, plus two self-check quizzes |

## Design

"Terminal corridor" — dark-first and technical. Charcoal ground (`#0D1117`), one electric-teal
accent (`#2DD4BF`), amber (`#F59E0B`) for known gaps and warnings. Mono is structural: eyebrows,
account codes, ledger figures. No glow, no gradients on text.

All of it is in `style.css`. The custom classes used throughout the MDX:

| Class | Meaning |
| --- | --- |
| `.arc-eyebrow` | Mono kicker above a page title (`--amber`, `--dim` variants) |
| `.arc-claim` | A load-bearing claim the code enforces — teal left rule |
| `.arc-gap` | A known limitation, stated rather than hidden — amber left rule |
| `.arc-symptom` | The opening symptom of an engineering story |
| `.arc-stats` / `.arc-stat` | Cited-figure strips |
| `.arc-cite` | Source line at the foot of a research page |

Keeping `.arc-claim` and `.arc-gap` used honestly is the site's main editorial rule: teal means
there is a test or a database constraint behind it, amber means there is not.

## Deploying

`docs.json` is at the repository root, so no content-directory override is needed.

1. Push this repository to `el-uno/fintech_doc`.
2. At [dashboard.mintlify.com](https://dashboard.mintlify.com), create a deployment and connect
   the `el-uno/fintech_doc` repository.
3. Leave the content directory as the repository root.
4. Deploys run on push to `main`.

## Local preview

```bash
npm i -g mint
```

```bash
mint dev
```

Serves on `http://localhost:3000`. `mint broken-links` checks internal links.

## Editorial conventions

- Money is always integer minor units in prose and tables. `10000n` is €100.00.
- Account codes appear as structured strings: `asset.float.bank.EUR`.
- Every research figure carries the body it came from and the date, so it can be re-checked
  rather than inherited. Secondary-aggregator figures are flagged as such in
  `primer/bibliography.mdx`.
- Pages describing planned work say so at the top. Nothing claims a capability the repo lacks.

## Keeping it accurate

Phase status appears in two places — `index.mdx` and `architecture/overview.mdx`. The pages most
likely to go stale as the build progresses:

| When this lands | Update |
| --- | --- |
| Prisma-backed `LedgerStore` | `architecture/ledger.mdx`, `architecture/testing.mdx` gaps |
| Holds wired at quote time | `architecture/ledger.mdx`, `architecture/settlement-saga.mdx` |
| Real `CompliancePort` replaces `AlwaysApprove` | `architecture/compliance.mdx` |
| Phase 6–8 | Status tables, `decisions/index.mdx` planned ADRs |
