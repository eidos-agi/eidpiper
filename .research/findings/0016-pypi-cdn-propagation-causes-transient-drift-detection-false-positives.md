---
id: '0016'
title: PyPI CDN propagation causes transient drift detection false positives
status: open
evidence: REASONED
sources:
- text: 'Direct experience: pypi_status showed GIT_AHEAD immediately after v0.4.0
    publish, IN_SYNC 30s later (content_hash:cdndelay)'
  tier: PRIMARY
created: '2026-04-03'
---

## Claim

After publishing ai-cockpit v0.4.0, railguey pypi_status briefly showed GIT_AHEAD because PyPI's CDN hadn't propagated the new version yet. eidpiper must account for CDN propagation delay when verifying the 'stamped' stage — retry/poll, don't single-check.

## Supporting Evidence

> **Source [PRIMARY]:** Direct experience: pypi_status showed GIT_AHEAD immediately after v0.4.0 publish, IN_SYNC 30s later (content_hash:cdndelay), retrieved 2026-04-03

## Caveats

None identified yet.
