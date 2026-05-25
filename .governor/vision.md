---
title: "eidpiper \u2014 Pipe code from source to users"
type: "vision"
date: "2026-04-03"
---

eidpiper manages the journey from code to users across a fleet of repos. It owns two things:

1. **The fleet's CI/CD infrastructure** — canonical workflow templates, synced to all repos, with drift detection and health reporting. No more copy-paste, no more inconsistencies, no more "this repo is missing publish.yml."

2. **The release pipeline** — orchestrates existing tools (foss-forge, ship-forge, railguey) into a gated sequence: readiness → correctness → publication → deployment. Tracks where each version is in the pipeline.

eidpiper does not replace GitHub Actions — it manages them. It does not replace forges — it composes them. It does not replace railguey — it calls it. The actions are the execution engine. The forges are the domain experts. eidpiper is the conductor.

## The Forgeline

```
foss-forge (legitimacy) → ship-forge (correctness) → eidpiper (artifact contract) → railguey (runtime truth)
```

Each stage gates the next. Each tool owns its concern. eidpiper owns the pipeline state and the workflow fleet.

## Why This Exists

- 20 repos with copy-pasted, inconsistent GitHub Actions workflows
- Manual propagation when a workflow improves (edit N repos by hand)
- Missing workflows in some repos
- No tool owns the full release sequence
- AI agents can't release packages without knowing which steps to run

## What eidpiper Is NOT

- Not a CI/CD platform (GitHub Actions is the platform)
- Not a build tool (ship-forge handles that)
- Not a deployment tool (railguey handles that)
- Not a compliance checker (foss-forge handles that)
- Not a god object (strict gate contract: pass/fail/pending, no forge-specific logic)
