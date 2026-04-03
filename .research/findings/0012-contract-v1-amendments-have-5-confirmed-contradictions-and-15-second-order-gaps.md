---
id: '0012'
title: 'Contract v1 amendments have 5 confirmed contradictions and 15 second-order
  gaps'
status: open
evidence: REASONED
sources:
- text: 'GPT-5.2 second-round adversarial review — 10 additional problems + 2 clarifying
    questions (content_hash:gpt52ad2)'
  tier: EXPERT
- text: 'Gemini 2.5 Pro adversarial review — confirmed all 5 contradictions + 5 additional
    (content_hash:gem25ad2)'
  tier: EXPERT
created: '2026-04-03'
---

## Claim

Second round of adversarial review found: (1) direct_commit to main is incompatible with branch protection — fundamental conflict; (2) skill adapter is unusable from CLI — abstraction leak from wrong execution model; (3) optimistic locking via hash + direct commit guarantees race conditions; (4) template pinning diverges from sync — code on disk isn't code that runs; (5) variables-only overrides can't express structural differences between repo types. Plus 15 second-order issues including: retry without attempt IDs, in-progress detection with no lease/expiry, audit trail loses human identity behind App, exit codes too few, PR force-push invalidates reviews, template pinning by CLI version is wrong key, gate registry is itself a drift surface, multiple pyproject.toml even in non-monorepos, pre-release without channels breaks rollback semantics, variables-only overrides create permanent drift.

## Supporting Evidence

> **Source [EXPERT]:** GPT-5.2 second-round adversarial review — 10 additional problems + 2 clarifying questions (content_hash:gpt52ad2), retrieved 2026-04-03
>
> **Source [EXPERT]:** Gemini 2.5 Pro adversarial review — confirmed all 5 contradictions + 5 additional (content_hash:gem25ad2), retrieved 2026-04-03

## Caveats

None identified yet.
