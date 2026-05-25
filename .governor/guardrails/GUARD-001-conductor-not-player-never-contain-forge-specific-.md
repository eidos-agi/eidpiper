---
id: "GUARD-001"
type: "guardrail"
title: "Conductor, not player \u2014 never contain forge-specific logic"
status: "active"
date: "2026-04-03"
---

eidpiper orchestrates tools, it does not contain their logic. Every pipeline stage must conform to a universal gate contract: { status: passed|failed|pending, message, artifacts }. The moment eidpiper has `if forge == 'foss-forge' and error_code == 42` it has become a god object. Fix the forge to conform to the contract instead.
