---
title: Full file sync — canonical templates copied to each repo
verdict: provisional
---

## What It Is

eidpiper owns canonical workflow files and copies them to each repo, like the existing bin/sync-skills pattern in ai-cockpit. Drift detection = SHA256 comparison. Updating = PR with the full file replacement. More flexible (each repo has the full workflow) but harder to manage (diff/merge conflicts, per-repo edits create drift).

## Validation Checklist

- [ ] Claim 1: Y — placeholder resolved
- [ ] Full file sync handles all workflow types including publish with trusted publisher: Y — each repo has its own publish.yml with id-token:write
- [ ] SHA256 comparison drift detection works reliably across all file types: Y — full files include the publish step natively, no reusable workflow limitation

## Scoring

_Not yet scored._
