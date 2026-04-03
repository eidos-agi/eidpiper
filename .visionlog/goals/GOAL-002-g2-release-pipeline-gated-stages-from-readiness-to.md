---
id: "GOAL-002"
type: "goal"
title: "G2: Release pipeline \u2014 gated stages from readiness to deployment"
status: "not_started"
date: "2026-04-03"
depends_on: ["G1: Fleet sync \u2014 canonical workflows synced to all repos with drift detection"]
unlocks: []
---

Orchestrate releases through: foss-forge (readiness) → ship-forge (correctness) → publish (PyPI) → railguey (deployment verification). Track release state in .eidpiper/release.yaml. Universal gate contract: pass/fail/pending. Depends on G1 because standardized workflows are what make the pipeline reliable.
