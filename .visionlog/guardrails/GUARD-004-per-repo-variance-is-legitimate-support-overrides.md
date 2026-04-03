---
id: "GUARD-004"
type: "guardrail"
title: "Per-repo variance is legitimate \u2014 support overrides"
status: "active"
date: "2026-04-03"
---

Not every repo is identical. Some need extra CI steps, different Python versions, or conditional publish logic. eidpiper must support a clean override mechanism (e.g. eidpiper.yaml per repo) so variance is declared, not hacked. Undeclared variance is drift. Declared variance is configuration.
