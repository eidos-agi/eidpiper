---
id: 0009
title: Reusable workflows have significant limitations for trusted publishing
status: open
evidence: REASONED
sources:
- text: 'https://docs.github.com/en/actions/sharing-automations/reusing-workflows
    (content_hash:ghreuse2)'
  tier: PRIMARY
- text: 'https://github.com/orgs/community/discussions/65766 — cross-org secrets discussion
    (content_hash:ghdisc65)'
  tier: SECONDARY
- text: 'https://docs.pypi.org/trusted-publishers/ — trusted publishing cannot be
    used from reusable workflows (content_hash:pypitpru)'
  tier: PRIMARY
created: '2026-04-03'
---

## Claim

Reusable workflows cannot use secrets: inherit across different organizations. GITHUB_TOKEN permissions can only be downgraded, not elevated, through the call chain. Environment secrets cannot be passed via workflow_call — they must be set at the job level in the called workflow. PyPI trusted publishing cannot be used from within a reusable workflow. These limitations mean the reusable-workflows candidate may not work cleanly for the publish step.

## Supporting Evidence

> **Source [PRIMARY]:** https://docs.github.com/en/actions/sharing-automations/reusing-workflows (content_hash:ghreuse2), retrieved 2026-04-03
>
> **Source [SECONDARY]:** https://github.com/orgs/community/discussions/65766 — cross-org secrets discussion (content_hash:ghdisc65), retrieved 2026-04-03
>
> **Source [PRIMARY]:** https://docs.pypi.org/trusted-publishers/ — trusted publishing cannot be used from reusable workflows (content_hash:pypitpru), retrieved 2026-04-03

## Caveats

None identified yet.
