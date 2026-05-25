---
id: "GUARD-005"
type: "guardrail"
title: "No secrets in templates or state files"
status: "active"
date: "2026-04-03"
---

Workflow templates must never contain secrets. PyPI tokens, Railway tokens, and API keys live in GitHub Actions environments and secrets. eidpiper state files (.eidpiper/) are committed to git and must never contain credentials.
