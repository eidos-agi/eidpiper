---
id: '0004'
title: 'The gate contract prevents god-object rot'
status: open
evidence: REASONED
sources:
- text: 'Gemini 2.5 Pro: ''define a strict Gate contract'' (content_hash:gem25gate)'
  tier: EXPERT
- text: 'GPT-5.2: ''be dogmatic about separation of concerns'' (content_hash:gpt52soc)'
  tier: EXPERT
- text: 'DeepSeek R1: agreed after pivot that composition is sound (content_hash:dsr1comp)'
  tier: EXPERT
created: '2026-04-03'
---

## Claim

Orchestrators become god objects when they contain stage-specific logic. The mitigation is a strict universal gate contract: every stage returns {status: passed|failed|pending, message, artifacts}. eidpiper never branches on which forge returned the result. All three consulted models independently converged on this pattern.

## Supporting Evidence

> **Source [EXPERT]:** Gemini 2.5 Pro: 'define a strict Gate contract' (content_hash:gem25gate), retrieved 2026-04-03
>
> **Source [EXPERT]:** GPT-5.2: 'be dogmatic about separation of concerns' (content_hash:gpt52soc), retrieved 2026-04-03
>
> **Source [EXPERT]:** DeepSeek R1: agreed after pivot that composition is sound (content_hash:dsr1comp), retrieved 2026-04-03

## Caveats

None identified yet.
