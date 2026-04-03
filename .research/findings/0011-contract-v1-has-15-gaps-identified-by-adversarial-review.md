---
id: '0011'
title: Contract v1 has 15+ gaps identified by adversarial review
status: open
evidence: REASONED
sources:
- text: 'GPT-5.2 adversarial review of eidpiper-v1.yaml — 10 prompted holes + 5 additional
    + cross-cutting contradictions (content_hash:gpt52adv)'
  tier: EXPERT
- text: 'DeepSeek R1 adversarial review — 9 concrete failure scenarios with code-level
    examples (content_hash:dsr1adv)'
  tier: EXPERT
created: '2026-04-03'
---

## Claim

Two independent adversarial reviews (GPT-5.2, DeepSeek R1) identified critical gaps in eidpiper-v1.yaml: (1) no timeout/retry for pending gates, (2) no concurrency/locking model, (3) state authority undefined (per-repo vs central), (4) no rollback/yank concept, (5) no monorepo support, (6) override format undefined, (7) drift status overlap (behind vs modified), (8) no error taxonomy, (9) template pinning per-release not recorded, (10) naming gates after specific forges violates conductor guardrail, (11) branch protection conflicts with force mode, (12) no PR dedup logic, (13) no pre-release version handling, (14) eidpiper needs credentials but says never store secrets, (15) no rate limit handling for fleet operations.

## Supporting Evidence

> **Source [EXPERT]:** GPT-5.2 adversarial review of eidpiper-v1.yaml — 10 prompted holes + 5 additional + cross-cutting contradictions (content_hash:gpt52adv), retrieved 2026-04-03
>
> **Source [EXPERT]:** DeepSeek R1 adversarial review — 9 concrete failure scenarios with code-level examples (content_hash:dsr1adv), retrieved 2026-04-03

## Caveats

None identified yet.
