---
id: '0010'
title: 'The central-actions pattern uses a shared repo with version tags'
status: open
evidence: REASONED
sources:
- text: 'https://github.com/kkacsh321/central-actions-example (content_hash:cenacex)'
  tier: PRIMARY
- text: 'https://github.blog/enterprise-software/devops/building-organization-wide-governance-and-re-use-for-ci-cd-and-automation-with-github-actions/
    (content_hash:ghgov01)'
  tier: PRIMARY
created: '2026-04-03'
---

## Claim

The established pattern for centralizing GitHub Actions is a shared repo (e.g. org/.github or org/actions-workflows) that contains reusable workflows referenced by version tag. Individual repos call these with workflow_call pinned to a ref. Updating = bump the ref. This is the recommended approach from GitHub's own documentation and multiple blog posts. The pattern works for CI/build but has friction for publish (trusted publisher limitation).

## Supporting Evidence

> **Source [PRIMARY]:** https://github.com/kkacsh321/central-actions-example (content_hash:cenacex), retrieved 2026-04-03
>
> **Source [PRIMARY]:** https://github.blog/enterprise-software/devops/building-organization-wide-governance-and-re-use-for-ci-cd-and-automation-with-github-actions/ (content_hash:ghgov01), retrieved 2026-04-03

## Caveats

None identified yet.
