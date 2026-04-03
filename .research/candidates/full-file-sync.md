---
title: Full file sync — canonical templates copied to each repo
verdict: provisional
---

## What It Is

eidpiper owns canonical workflow files and copies them to each repo, like the existing bin/sync-skills pattern in ai-cockpit. Drift detection = SHA256 comparison. Updating = PR with the full file replacement. More flexible (each repo has the full workflow) but harder to manage (diff/merge conflicts, per-repo edits create drift).

## Validation Checklist

- [ ] Claim 1: _TBD_

## Scoring

_Not yet scored._
