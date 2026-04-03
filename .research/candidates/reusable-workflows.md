---
title: Reusable workflows — thin stubs + central canonical workflows
verdict: provisional
---

## What It Is

Each repo gets a thin stub workflow (5-10 lines) that calls a central reusable workflow via workflow_call pinned to a version tag. eidpiper manages the stubs and version pins. Drift detection = is the stub pinned to latest? Updating = bump the pin. GPT-5.2's recommended approach.

## Validation Checklist

- [ ] Claim 1: Y — placeholder resolved
- [ ] Reusable workflows can handle the publish step via trusted publisher: N — Finding 0009 proves this is impossible
- [ ] Drift detection is trivial with reusable workflows (just check version pin): N — Finding 0009: PyPI trusted publishing CANNOT be used from within a reusable workflow. Per-repo publish stubs are still required.

## Scoring

_Not yet scored._
