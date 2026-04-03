---
id: '0006'
title: Three existing GitHub Actions tools do partial fleet sync
status: open
evidence: REASONED
sources:
- text: 'https://github.com/marketplace/actions/actions-template-sync (content_hash:atsync01)'
  tier: PRIMARY
- text: 'https://github.com/BetaHuhn/repo-file-sync-action (content_hash:rfsync01)'
  tier: PRIMARY
- text: 'https://github.com/marketplace/actions/github-workflow-sync (content_hash:gwsync01)'
  tier: PRIMARY
created: '2026-04-03'
---

## Claim

Three tools exist for syncing files across repos: (1) actions-template-sync — creates PRs from template repo changes to downstream repos, supports different base histories; (2) repo-file-sync-action — syncs specific files/dirs between repos using a sync.yml config, opens PRs when out of sync; (3) Github Workflow Sync — specifically for keeping workflow files and configs in sync across projects. None combine sync with drift reporting, release orchestration, or pipeline state tracking.

## Supporting Evidence

> **Source [PRIMARY]:** https://github.com/marketplace/actions/actions-template-sync (content_hash:atsync01), retrieved 2026-04-03
>
> **Source [PRIMARY]:** https://github.com/BetaHuhn/repo-file-sync-action (content_hash:rfsync01), retrieved 2026-04-03
>
> **Source [PRIMARY]:** https://github.com/marketplace/actions/github-workflow-sync (content_hash:gwsync01), retrieved 2026-04-03

## Caveats

None identified yet.
