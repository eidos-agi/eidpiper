---
id: '0013'
title: PyPI trusted publisher fails after repo rename
status: open
evidence: CONFIRMED
sources:
- text: 'Direct experience: this session, v0.3.0 publish failed after repo rename
    (content_hash:v030fail)'
  tier: PRIMARY
- text: 'GitHub Actions run 23954565697 — publish failure log showing ''valid token,
    but no corresponding publisher'' (content_hash:ghrun030)'
  tier: PRIMARY
disconfirmation: 'Searched for automatic trusted publisher migration on rename. GitHub
  auto-redirects repo URLs but PyPI OIDC claims use the current repo name, not redirects.
  There is no automatic fix.'
created: '2026-04-03'
---

## Claim

When ai-cockpit-template was renamed to ai-cockpit on GitHub, the trusted publisher configuration on PyPI still referenced the old repo name. The publish workflow ran successfully but PyPI rejected the OIDC token with 'invalid-publisher: Publisher with matching claims was not found'. The fix required manually updating the publisher on pypi.org. eidpiper must detect this class of failure and surface it clearly.

## Supporting Evidence

> **Source [PRIMARY]:** Direct experience: this session, v0.3.0 publish failed after repo rename (content_hash:v030fail), retrieved 2026-04-03
>
> **Source [PRIMARY]:** GitHub Actions run 23954565697 — publish failure log showing 'valid token, but no corresponding publisher' (content_hash:ghrun030), retrieved 2026-04-03

## Disconfirmation Search

Searched for automatic trusted publisher migration on rename. GitHub auto-redirects repo URLs but PyPI OIDC claims use the current repo name, not redirects. There is no automatic fix.

## Caveats

None identified yet.
