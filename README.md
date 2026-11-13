# Chase Baker

I run a trading-card business (ChasingCards) and build the software that runs it: optimization for what to buy and how to price it, decision models for what to grade, agent workflows with human approval gates for store operations, and the measurement to know whether any of it works. USC Computer Science & Business, Dec 2026.

My rule for AI systems is that they are **measured before they are trusted** — tested scripts compute every number, models orchestrate and classify, humans hold the approval gates, and every claim ships with the experiment that backs it.

## Where to start, by what you're hiring for

| You care about | Start here | Try it (60 s) |
|---|---|---|
| AI agents (tool use, gates, exactly-once, evals) | cardshop-agents — in progress, link added when it's public | — |
| ML (model selection, validation, calibration) | [cardsegments](https://github.com/chasebak/cardsegments) | [Buy List Explorer](https://chasebak.github.io/cardsegments/) |
| Optimization under uncertainty | [milo](https://github.com/chasebak/milo) | [Restock Explorer](https://chasebak.github.io/milo/) |
| Decisions under uncertainty / ROI | [grace-grading-roi](https://github.com/chasebak/grace-grading-roi) | [Hand GRACE a Budget](https://chasebak.github.io/grace-grading-roi/) |
| Estimation from partial data / forecasting | [ordergaps](https://github.com/chasebak/ordergaps) | [Gap Explorer](https://chasebak.github.io/ordergaps/) |

Every number on these pages is computed by the repo's tested Python; the pages only display it.

## The repos

- **[milo](https://github.com/chasebak/milo)** — the production restock + pricing optimizer behind my business: a two-stage stochastic MILP (Pyomo GDP → HiGHS) with gamma-Poisson demand shrinkage, kinked elasticities, an out-of-sample scorecard, and a constraint ladder that prices each real business rule. On demand it never saw, the optimizer returns 0.786 per restock dollar vs 0.763 for a careful greedy list (synthetic).
- **cardshop-agents** (in progress) — the agent that runs my consignment operation, rebuilt clean-room on a synthetic storefront: a tool-use loop where code owns the step order, one approval gate per run, a vendor scope bound in code, exactly-once bookkeeping, and 30 incident-based eval tasks graded on the end state. It goes public once its real model runs are recorded.
- **[cardsegments](https://github.com/chasebak/cardsegments)** — segmentation and a pre-registered grouped k-fold model ladder for graded-card liquidity, with leakage checks, null controls and a parked-capital KPI at a cost-derived threshold. Synthetic data; real-data results stay private.
- **[grace-grading-roi](https://github.com/chasebak/grace-grading-roi)** — should you grade this card? NPV-per-dollar ranking with partial-pooled gem rates, data-quality gates tested as a classifier, and a budget backtest against an exact-knapsack oracle: GRACE captures 0.857 of the best batch's value vs 0.336 for a common heuristic (synthetic).
- **[ordergaps](https://github.com/chasebak/ordergaps)** — how big is the whole store? Exact sequential order-number arithmetic, a temporal allocation model, and a leak-free rolling forecast backtest, all validated against a simulator with ground truth.
- **[Collectors (private) — case study](collectors-case-study.md)** — the FastAPI + SQLite app behind my card decisions: OpenCV centering, a local vision gate, GRACE and price movers, with 396 test files and CI. Private; walkthrough on request.

These are public re-implementations and studies drawn from my private production systems, built in October–November 2026 with the same Claude Code agent workflows my resume describes — the velocity is part of the point. Production data stays private; every repo runs end to end on synthetic data, and real-data results appear only as labeled aggregates.
