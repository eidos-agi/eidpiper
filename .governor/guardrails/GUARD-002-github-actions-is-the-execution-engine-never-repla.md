---
id: "GUARD-002"
type: "guardrail"
title: "GitHub Actions is the execution engine \u2014 never replace it"
status: "active"
date: "2026-04-03"
---

eidpiper manages workflows, it does not run builds. The actual CI/CD execution happens in GitHub Actions. eidpiper syncs templates, detects drift, triggers workflows, and reads results. It never runs `pytest`, `python -m build`, or `twine upload` itself outside of GitHub Actions.
