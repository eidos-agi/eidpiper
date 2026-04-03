---
id: '0015'
title: CHANGELOG validation catches real errors but format must be consistent
status: open
evidence: CONFIRMED
sources:
- text: 'Direct experience: CI guardrails added to 3 repos using grep pattern ''##
    v${TAG_VERSION}'' (content_hash:ciguard)'
  tier: PRIMARY
- text: 'Contract v1 includes changelog_format as a template variable — already planned
    (content_hash:ctrctv1)'
  tier: PRIMARY
disconfirmation: 'Checked all 6 Eidos PyPI package CHANGELOGs — all use ''## v'' format
  currently. But eidos-mail has no CHANGELOG at all.'
created: '2026-04-03'
---

## Claim

The CI guardrail greps for '## v${TAG_VERSION}' in CHANGELOG.md. This works for all Eidos repos today but depends on a consistent heading format. A repo that uses '## 0.4.0' (no 'v' prefix) or '### v0.4.0' (wrong heading level) will fail. eidpiper must either enforce the format or make the grep pattern configurable per-repo.

## Supporting Evidence

> **Source [PRIMARY]:** Direct experience: CI guardrails added to 3 repos using grep pattern '## v${TAG_VERSION}' (content_hash:ciguard), retrieved 2026-04-03
>
> **Source [PRIMARY]:** Contract v1 includes changelog_format as a template variable — already planned (content_hash:ctrctv1), retrieved 2026-04-03

## Disconfirmation Search

Checked all 6 Eidos PyPI package CHANGELOGs — all use '## v' format currently. But eidos-mail has no CHANGELOG at all.

## Caveats

None identified yet.
