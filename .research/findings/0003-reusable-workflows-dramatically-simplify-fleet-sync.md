---
id: '0003'
title: Reusable workflows dramatically simplify fleet sync
status: open
evidence: REASONED
sources:
- text: 'GPT-5.2 consultation: ''prefer reusable workflows over copying full workflow
    bodies'' (content_hash:gpt52rw)'
  tier: EXPERT
- text: 'https://docs.github.com/en/actions/sharing-automations/reusing-workflows
    (content_hash:ghreuse)'
  tier: PRIMARY
created: '2026-04-03'
---

## Claim

GitHub reusable workflows (workflow_call) allow each repo to have a thin stub that calls a central canonical workflow pinned to a version tag. Drift detection becomes trivial: is the stub pinned to latest? Updating becomes trivial: bump the pin. This eliminates diff/merge conflicts from full file sync. GPT-5.2 strongly recommended this approach.

## Supporting Evidence

> **Source [EXPERT]:** GPT-5.2 consultation: 'prefer reusable workflows over copying full workflow bodies' (content_hash:gpt52rw), retrieved 2026-04-03
>
> **Source [PRIMARY]:** https://docs.github.com/en/actions/sharing-automations/reusing-workflows (content_hash:ghreuse), retrieved 2026-04-03

## Caveats

None identified yet.
