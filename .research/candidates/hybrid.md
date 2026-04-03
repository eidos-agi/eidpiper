---
title: 'Hybrid — reusable workflows for standard stages, full sync for custom'
verdict: provisional
---

## What It Is

Use reusable workflows for the standard pipeline (ci, publish) but allow repos to have additional custom workflows that eidpiper doesn't manage. eidpiper tracks which workflows are managed vs custom. Combines the low-drift benefits of reusable workflows with the flexibility of repo-local customization.

## Validation Checklist

- [ ] Claim 1: Y — placeholder resolved
- [ ] Hybrid approach avoids the trusted publisher limitation of pure reusable workflows: Y — publish stays as full file, CI uses reusable workflow
- [ ] Custom workflows outside managed set don't create permanent drift: Y — publish stays as full file (avoids reusable workflow limitation), CI uses reusable workflow

## Scoring

_Not yet scored._
