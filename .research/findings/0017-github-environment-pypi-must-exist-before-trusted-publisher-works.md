---
id: '0017'
title: GitHub environment 'pypi' must exist before trusted publisher works
status: open
evidence: REASONED
sources:
- text: 'Direct experience: manually created pypi environment via gh api for ai-cockpit
    (content_hash:ghenvpypi)'
  tier: PRIMARY
created: '2026-04-03'
---

## Claim

The publish.yml workflow references 'environment: pypi'. If this environment doesn't exist, the workflow fails with a confusing OIDC error. eidpiper doctor should verify the pypi environment exists for every repo with a publish.yml.

## Supporting Evidence

> **Source [PRIMARY]:** Direct experience: manually created pypi environment via gh api for ai-cockpit (content_hash:ghenvpypi), retrieved 2026-04-03

## Caveats

None identified yet.
