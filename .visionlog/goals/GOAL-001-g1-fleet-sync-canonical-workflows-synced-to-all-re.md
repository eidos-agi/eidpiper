---
id: "GOAL-001"
type: "goal"
title: "G1: Fleet sync \u2014 canonical workflows synced to all repos with drift detection"
status: "not_started"
date: "2026-04-03"
depends_on: []
unlocks: []
---

Define canonical workflow templates (ci.yml, publish.yml). Sync to all repos in the org. Detect drift (repo's workflow differs from canonical). Report fleet health (N/M repos current, X behind, Y missing). Support per-repo overrides via eidpiper.yaml. This is the MVP.
