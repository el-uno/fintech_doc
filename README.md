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
