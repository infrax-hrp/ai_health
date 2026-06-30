# ai_health — outbreak signal recovery

> The aim for this AI in Health study plan is depth: genuinely acquiring MLOps, LLM
> engineering, and deep-learning skills.

This repo is the artifact that makes that learning concrete.

> **Goal (one sentence):** Recover a hidden disease outbreak from a pile of noisy,
> natural-language field notes — and flag the affected districts with calibrated uncertainty.

I simulate an outbreak, bury it in noisy natural-language surveillance notes, then build a
monitored pipeline that recovers the signal and flags the cluster with calibrated
uncertainty — benchmarking a **fine-tuned encoder** against a **frontier LLM** on the
extraction step.

## Why this project

A learning artifact that exercises three skills end to end:

1. **Production ML / MLOps** — containerization, CI/CD, deployment, monitoring.

2. **Production-grade LLM engineering** — structured extraction, rigorous evals, cost/latency control.

3. **Modern deep learning** — fine-tuning an encoder (BERT-family) as a real component.

The differentiator is a rigorous **evaluation harness** and a **statistical aggregation
layer** (cluster/anomaly detection with uncertainty) — the parts that need epidemiological
judgement, not just engineering.

## How it works (two-layer design)

- **Truth layer** — a small stochastic simulation generates an outbreak as structured
  parameters (pathogen, ~5–8 districts, ~12-week window, per-district case trajectories).
  Some districts carry a real rising signal; the rest stay at baseline noise.
- **Text layer** — each report is rendered as a realistic, noisy surveillance note
  (varied phrasing, inconsistent dates, missing fields, typos, indirect locations).

Because we plant the truth, **every stage is measurable against known ground truth** —
which is what makes the evaluation rigorous rather than a judgement call.

```
noisy notes  →  extract structured fields  →  reassemble clean dataset  →  detect cluster
                (LLM  +  fine-tuned encoder)                              (with uncertainty)
```

**Extraction schema (v1):** `pathogen`, `location`, `report_date`, `case_count`, `severity_flag`.

## Data

All data is **synthetic and self-generated** — no real or sensitive data. This keeps the
repo public-safe and gives exact ground truth for evaluation.

## Status

🚧 Week 1 — project scaffolding. The build runs in weekly units; roadmap below.

| Phase | Weeks | Focus |
|------|-------|-------|
| Foundations & framing | 1–5 | MLOps mindset, containers, LLM rigor, deep-learning fundamentals, spec |
| Build the artifact | 6–13 | Generator, LLM extraction, **eval harness**, fine-tuned encoder, bake-off, **stats layer**, serve, deploy, monitor |
| Harden & show | 14–16 | Dashboard, docs, write-up |

## License

TBD.
