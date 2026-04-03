---
id: '0007'
title: OpenSSF Allstar enforces security policies across GitHub orgs
status: open
evidence: REASONED
sources:
- text: 'https://github.com/ossf/allstar (content_hash:allstar1)'
  tier: PRIMARY
- text: 'https://openssf.org/blog/2021/08/11/introducing-the-allstar-github-app/ (content_hash:allstblog)'
  tier: PRIMARY
created: '2026-04-03'
---

## Claim

Allstar is a GitHub App by the Open Source Security Foundation that continuously checks GitHub API states and repo file contents against defined security policies and takes enforcement actions (file issues, change settings, log). It checks workflow configuration files for compliance with org-level rules. However, it's security-focused (branch protection, SECURITY.md, etc), not workflow template management or release pipeline orchestration.

## Supporting Evidence

> **Source [PRIMARY]:** https://github.com/ossf/allstar (content_hash:allstar1), retrieved 2026-04-03
>
> **Source [PRIMARY]:** https://openssf.org/blog/2021/08/11/introducing-the-allstar-github-app/ (content_hash:allstblog), retrieved 2026-04-03

## Caveats

None identified yet.
