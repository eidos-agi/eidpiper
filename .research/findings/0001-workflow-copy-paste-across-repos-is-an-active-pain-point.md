---
id: '0001'
title: 'Workflow copy-paste across repos is an active pain point'
status: open
evidence: CONFIRMED
sources:
- text: 'Direct experience: this session, 2026-04-03, edited publish.yml in 3 repos
    (content_hash:sessn403)'
  tier: PRIMARY
- text: 'DeepSeek R1 graded pivot 8.5/10 specifically citing this as painkiller (content_hash:dsr1pvt)'
  tier: EXPERT
disconfirmation: 'Searched for arguments that copy-paste is fine. At small scale (3
  repos) it''s tolerable. But at 6+ PyPI packages and 20 repos, it''s already causing
  inconsistencies. The pain scales linearly with repo count.'
created: '2026-04-03'
---

## Claim

Adding CI guardrails to 3 repos required manually editing each publish.yml individually. Workflows have inconsistencies: ai-cockpit lacks contents:read, railguey has it, apple-a-day has detailed comments others lack. eidos-mail has no publish.yml at all. This pain was experienced directly during this session.

## Supporting Evidence

> **Source [PRIMARY]:** Direct experience: this session, 2026-04-03, edited publish.yml in 3 repos (content_hash:sessn403), retrieved 2026-04-03
>
> **Source [EXPERT]:** DeepSeek R1 graded pivot 8.5/10 specifically citing this as painkiller (content_hash:dsr1pvt), retrieved 2026-04-03

## Disconfirmation Search

Searched for arguments that copy-paste is fine. At small scale (3 repos) it's tolerable. But at 6+ PyPI packages and 20 repos, it's already causing inconsistencies. The pain scales linearly with repo count.

## Caveats

None identified yet.
