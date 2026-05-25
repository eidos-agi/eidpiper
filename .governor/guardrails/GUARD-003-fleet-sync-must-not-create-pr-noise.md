---
id: "GUARD-003"
type: "guardrail"
title: "Fleet sync must not create PR noise"
status: "active"
date: "2026-04-03"
---

When syncing workflows to repos, eidpiper must batch changes, support report-only mode, and allow per-repo opt-out. A tool that opens 20 PRs every time a comment changes in a template will be disabled by the second day. Respect the repos it manages.
