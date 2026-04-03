# eidpiper — Session Handoff (2026-04-03)

> Read this before doing anything. This is the complete context for where eidpiper stands.

## What eidpiper Is

A GitHub Actions fleet manager + release pipeline orchestrator for the Eidos AGI ecosystem (~20 repos, ~6 PyPI packages). Two jobs:

1. **Fleet sync** — manage canonical workflow templates, sync to all repos, detect drift, report health
2. **Release pipeline** — orchestrate: foss-forge (ready?) → ship-forge (sound?) → publish (stamped?) → railguey (live?)

CLI first. MCP server later. Composes existing tools, doesn't replace them.

## How We Got Here

This started as a cockpit-eidos session that went deep. The journey:

1. **ai-cockpit packaging** — packaged the `cockpit` CLI as `pip install ai-cockpit`, published v0.1.0 → v0.4.0 to PyPI
2. **Lifecycle redesign** — 4 primitives: takeoff → touch-and-go → can-i-close → land
3. **forge-forge MCP** — added `forge_how` and `forge_for_project` tools for forge discovery
4. **railguey PyPI awareness** — added `type: pypi_package` to service registry, drift detection, doctor integration
5. **Release pipeline research** — trilogy (research.md → visionlog → ike) in railguey produced ADR-001: minimal fix + railguey artifact tracking, reject semantic-release
6. **eidpiper conceived** — originally "release-forge", pivoted to "GitHub Actions fleet manager + release pipeline" after DeepSeek R1 graded the original idea 5/10 (vitamin not painkiller)
7. **The pivot** — fleet sync is the real pain (copy-paste workflows across repos). DeepSeek re-graded 8.5/10 after pivot. GPT-5.2 agreed at 8/10.
8. **Contract written** — `contracts/eidpiper-v1.yaml` specifies all three domains (Fleet, Pipeline, State)
9. **Two rounds of adversarial review** — GPT-5.2, Gemini 2.5 Pro, DeepSeek R1 attacked the contract. Found 5 fundamental contradictions. All fixed.

## Research State (17 findings, not yet decided)

The research project is at `research` phase. Criteria not locked, not scored, not decided.

### Three Candidates
| Candidate | Status | Key Issue |
|-----------|--------|-----------|
| **Reusable workflows** (thin stubs + central workflows) | Has a FAILED claim | Finding 0009: trusted publishing CANNOT work from reusable workflows. Publish step still needs per-repo files. |
| **Full file sync** (copy canonical files to each repo) | All claims pass | Works for everything including publish. But creates diff/merge friction and false-positive drift on whitespace. |
| **Hybrid** (reusable for CI, full file for publish) | All claims pass | Best of both: low-drift CI via reusable workflows, trusted publishing via full files. Most complex to implement. |

### Critical Findings (the ones that matter most)

**From web research:**
- 0009: Reusable workflows can't do PyPI trusted publishing (kills pure reusable-workflows candidate)
- 0008: GitHub is building centralized workflow governance in their 2026 roadmap (directionally similar but scoped to security, not release)
- 0006: Three existing tools do partial fleet sync (actions-template-sync, repo-file-sync-action, workflow-sync) — none combine with release orchestration

**From real PyPI release failures this session:**
- 0013: Trusted publisher fails after repo rename (ai-cockpit-template → ai-cockpit broke publishing)
- 0014: Dual-file version sync causes errors (fixed with importlib.metadata across 3 repos)
- 0015: CHANGELOG format must be consistent for grep-based validation
- 0016: PyPI CDN propagation causes 30-second false positives in drift detection
- 0017: GitHub 'pypi' environment must exist before trusted publisher works

**From adversarial contract review:**
- 0011: 15+ gaps in original contract (timeout, concurrency, state authority, rollback, monorepo, overrides, etc.)
- 0012: 5 fundamental contradictions in the amendments (state vs branch protection, skill adapter unusable from CLI, optimistic locking races, template pinning by wrong key, overrides too restrictive)

## Contract State (v1 + 2 rounds of fixes)

`contracts/eidpiper-v1.yaml` — fully specified. Three domains:

**Fleet:** registry of repos, canonical templates with variables, sync (dry-run/PR/force), drift detection (current/behind/missing/modified), health reporting.

**Pipeline:** 4 gated stages (ready → sound → stamped → live), universal gate contract (passed/failed/pending), advance/release commands, stages reference gate IDs via adapter registry (script/workflow/mcp/webhook).

**State:** lives in eidpiper's own repo (NOT managed repos — branch protection conflict resolved), lease-based locking with 30min expiry, actor identity preserved, template SHA pinned per release.

**Key amendments from adversarial review:**
- State moved from managed repos to eidpiper's own repo (branch protection incompatibility)
- Gate adapters: script/workflow/mcp/webhook (not "skill" which is Claude Code only)
- Overrides: 3 levels (variables, template selection, extra steps) — not variables-only
- Template pinning: commit SHA not CLI version
- Concurrency: lease-based with expiry + break-glass, not optimistic hash
- Retry: attempt IDs, publish checks PyPI before retrying (non-idempotent gate)
- Rollback: yank/supersede/abandon (append-only, never rewrite)
- Error taxonomy: 8 exit codes
- PR dedup: deterministic branch naming, force-push to existing
- Dangling override detection in sync --dry-run

## Visionlog State

- **Vision:** "Pipe code from source to users"
- **5 guardrails:** conductor not player, GHA is engine, no PR noise, support overrides, no secrets
- **3 goals:** G1 fleet sync (MVP) → G2 release pipeline → G3 MCP server
- **0 ADRs** — the architecture decision hasn't been made yet (research not completed)

## What To Do Next

**Complete the research (the decision hasn't been earned):**
1. Write decision criteria (implementation_effort, correctness, maintainability, ecosystem_fit, risk — same as railguey's research)
2. Lock criteria
3. Peer review the 17 findings
4. Score all 3 candidates — Finding 0009 strongly favors hybrid
5. Record decision → ADR in visionlog
6. Create tasks in ike from the contract's three domains

**Then build (fleet sync MVP first):**
7. Define canonical templates (ci.yml, publish.yml) from the best existing versions (apple-a-day has the best comments)
8. Build `eidpiper sync --dry-run` first — drift report without any changes
9. Build `eidpiper drift` and `eidpiper health`
10. Test against all 20 Eidos repos
11. Then `eidpiper sync --pr` — actually open PRs
12. Release pipeline is V2 after fleet sync is proven

## Repos Touched This Session

| Repo | What happened |
|------|--------------|
| ai-cockpit (renamed from ai-cockpit-template) | Packaged CLI, published v0.1.0→v0.4.0, lifecycle skills, loss-forge, completions, PROJECT-GUIDE, forge ecosystem |
| eidos-mail | Security audit (passed), published v0.1.0 to PyPI, marketplace plugin |
| eidos-marketplace | Added eidos-mail plugin |
| cockpit-eidos | Devlogs, memory updates |
| forge-forge | forge_how + forge_for_project MCP tools, enriched registry, installed.yaml spec, manifest v2, PLAN-0001 |
| loss-forge | /loss-init now stamps .forge/installed.yaml |
| railguey | PyPI research via trilogy, ADR-001, pypi_package type, drift detection, doctor integration, CI guardrails |
| eidpiper | NEW — repo created, full trilogy, contract v1 + 2 rounds adversarial review, 17 research findings |

## Key Decisions Already Made (in other repos, not eidpiper)

- **ADR-001 (railguey):** importlib.metadata for version, CI guardrails, pypi_package in registry. Reject semantic-release.
- **PLAN-0001 (forge-forge):** forge discovery + provenance. forge_how/forge_for_project tools. .forge/installed.yaml spec.
- **Cockpit lifecycle:** 4 primitives (takeoff/touch-and-go/can-i-close/land). Never suggest /land unprompted.

## LLM Consultations (4 models, 8+ conversations)

| Model | Topic | Grade/Verdict |
|-------|-------|---------------|
| Gemini 2.5 Pro | railguey PyPI awareness | Recommended, flagged race conditions |
| GPT-5.2 | railguey PyPI awareness | Recommended, flagged "pragmatic not lazy" |
| GPT-5.2 | Release pipeline (original) | 8/10 — create release-forge |
| Gemini 2.5 Pro | Release pipeline (original) | 7.5/10 — vitamin not painkiller |
| DeepSeek R1 | Release pipeline (original) | 5/10 — don't build, inventing a problem |
| GPT-5.2 | Release pipeline (pivot) | 8/10 — fleet sync is the killer feature |
| DeepSeek R1 | Release pipeline (pivot) | 8.5/10 — painkiller, no direct competitor |
| GPT-5.2 | Contract adversarial review round 1 | 15+ gaps found |
| Gemini 2.5 Pro | Contract adversarial review round 2 | 5 contradictions confirmed |
| GPT-5.2 | Contract adversarial review round 2 | 10 second-order problems found |
