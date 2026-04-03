---
id: '0014'
title: 'Version must be bumped in pyproject.toml ONLY — dual-file sync causes release
  errors'
status: open
evidence: CONFIRMED
sources:
- text: 'Direct experience: this session, TASK-0001 fixed version SSoT across 3 repos
    (content_hash:task0001)'
  tier: PRIMARY
- text: 'ADR-001 in railguey visionlog — research finding 0004 (content_hash:adr001f4)'
  tier: PRIMARY
disconfirmation: 'Some projects intentionally use dual-file versioning for Python
  3.7 compatibility. Irrelevant for Eidos ecosystem (requires >=3.10).'
created: '2026-04-03'
---

## Claim

ai-cockpit originally required version bumps in both pyproject.toml and __init__.py. This caused sync errors and was flagged as a loss function (L5). The fix — importlib.metadata.version() — was applied to 3 repos (ai-cockpit, railguey, apple-a-day). eidpiper's CI guardrail validates tag == pyproject.toml version. Any repo using dual-file versioning will fail the guardrail until fixed.

## Supporting Evidence

> **Source [PRIMARY]:** Direct experience: this session, TASK-0001 fixed version SSoT across 3 repos (content_hash:task0001), retrieved 2026-04-03
>
> **Source [PRIMARY]:** ADR-001 in railguey visionlog — research finding 0004 (content_hash:adr001f4), retrieved 2026-04-03

## Disconfirmation Search

Some projects intentionally use dual-file versioning for Python 3.7 compatibility. Irrelevant for Eidos ecosystem (requires >=3.10).

## Caveats

None identified yet.
