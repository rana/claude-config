# System

A personal cognitive toolkit for Claude Code. 33 skills, 9 commands. Skill definitions are read by AI — specific language in each prompt produces measurably different analytical behavior. This isn't configuration. It's cognitive infrastructure.

## Commands

| Command | Purpose |
|---------|---------|
| `/explore` | Deep multi-dimensional perspective |
| `/explore-act` | Same, biased toward action — produces change lists |
| `/calibrate` | Set session thinking parameters (directness, resolution, mode, speculation, craft, output shape) |
| `/commit` | Draft message, stage, commit, push |
| `/park` | Save work state and mental context for later |
| `/resume` | Restore parked context and present briefing |
| `/morning` | Daily development briefing — branches, PRs, activity, suggested focus |
| `/compose` | Chain skills in sequence, threading context forward |
| `/arc-gate` | Phase-appropriate quality gate — selects the right skill chain |

## Selection

Start from the situation, not the skill name. "Quick" is a single invocation. "Pipeline" is a `/compose` chain.

| Situation | Quick | Pipeline |
|-----------|-------|----------|
| How big is this change? | `/scope` | `scope, consequences, deep-review` |
| What happens if we do this? | `/consequences` | `steelman, consequences, gaps` |
| Should we change this? | `/steelman` | `steelman, inversion, consequences` |
| What's missing? | `/gaps` | `archaeology --layers F2, gaps` |
| Spec this for implementation | `/implement` | `implement` then build then `verify` |
| Does code match the spec? | `/verify` | — |
| Are the documents healthy? | `/doc-health` | `drift-detect, doc-health, crystallize` |
| Is this quality-ready? | `/deep-review` | `deep-review, crystallize` |
| Is this secure? | `/threat-model` | `threat-model, hardening-audit, ghost` |
| What would break? | `/ghost` | `ghost, incident-ready` |
| Why does this exist? | `/why-chain` | — |
| X or Y? | `/triad` | `triad, steelman, crystallize` |
| Something feels wrong | `/cognitive-debug` | `cognitive-debug, reframe, archaeology --layers F9` |
| What aren't we seeing? | `/reframe` | `reframe, gaps, consequences` |
| Is this over-engineered? | `/crystallize` | `steelman, crystallize` |
| Ready to ship? | `/launch-gate` | `ghost, threat-model, launch-gate` |
| What breaks at 2am? | `/ghost` | `ghost, incident-ready, ops-review` |
| How's the API surface? | `/api-review` | — |
| Trace this workflow | `/workflow-trace` | `workflow-trace, gaps, docs-quality` |
| Orient me to this area | `/context-switch` | — |

## Composition

`/compose` chains skills in sequence, threading context forward. Each skill sees what previous passes discovered.

### Principles

- **Order matters.** Perception-expanding skills (archaeology, reframe) before analytical skills (gaps, threat-model). Simplification (crystallize) last.
- **Three is the sweet spot.** Two is a focused pair. Three is a productive pipeline. Four+ risks context dilution — each skill processes more noise from previous passes.
- **Threading vs. independent.** Compose threads context — `/compose steelman, inversion` gives steelman-informed inversion. Running them separately gives two independent views. Choose based on whether you want cross-pollination or fresh perspectives.
- **Dialogue is incompatible with compose.** Compose needs autonomous passes. Use `--dialogue` for standalone deep dives where your mid-stream input changes quality of output.
- **Not everything composes.** `/context-switch`, `/scratch`, `/calibrate` are navigation or routing tools — they don't produce findings to thread forward.

### Decisions & Strategy

```bash
# Full strategic analysis — excavate, map tension, propagate, simplify
/compose archaeology, triad, consequences, crystallize : "the decision"

# Quick stress test — defend, attack, find what survives
/compose steelman, inversion, gaps : "the current approach"

# Tension resolution — map it, defend both sides, cut to essential
/compose triad, steelman, crystallize : "X vs Y"

# Assumption excavation — surface, flip, find gaps
/compose archaeology --layers F2, inversion, gaps : "the assumption"

# Forward propagation with cognitive preparation
/compose archaeology, triad, consequences : "the direction we're leaning"
```

### Quality & Review

```bash
# Analytical pipeline — size, propagate, gate
/compose scope, consequences, deep-review : "the proposed change"

# Design review with cognitive depth
/compose archaeology --layers F4,F11, deep-review : "the design"

# Document health (single-pass alternative: just run /doc-health)
/compose drift-detect, coherence, garden : "the project"

# Newcomer audit — can someone new navigate this?
/compose workflow-trace, gaps, docs-quality : "new developer onboarding"
```

### Security & Production

```bash
# Security sweep — systematic, technical, hidden
/compose threat-model, hardening-audit, ghost : "the system"

# Production readiness pipeline
/compose ops-review, incident-ready, launch-gate : "Phase N"

# Security with cognitive preparation — surface assumptions first
/compose archaeology --layers F2,F7, threat-model, hardening-audit : "the system"

# Supply chain with hidden dependency surfacing
/compose ghost, supply-chain-audit : "our dependency tree"

# Pre-launch — what breaks when this hits production?
/compose ghost, threat-model, launch-gate : "Phase N deployment"

# The defender's audit — build the case, then attack it
/compose steelman, threat-model, inversion : "our security posture"
```

### Implementation & Knowledge

```bash
# Design to verified code
/compose implement, verify : "DES-NNN or deliverable"

# Post-implementation knowledge capture — before context evaporates
/compose why-chain, tomorrow, ghost : "the module we just built"

# Risk map for "small" changes — size it, find hidden deps, propagate
/compose scope, ghost, consequences : "the proposed change"
```

### Architecture & Maintenance

```bash
# Periodic health check
/compose drift-detect, deep-review, crystallize : "the project"

# Entropy audit — stated vs actual, doc consistency, identifier lifecycle
/compose drift-detect, coherence, garden : "the project"
```

### Unblocking

```bash
# Break out of analysis paralysis
/compose cognitive-debug, reframe, archaeology --layers F9 : "the stuck point"

# Spatial sweep when conventional analysis produces nothing
/compose reframe, gaps, consequences : "the subject"
```

## Cognitive Quick Reference

Four skills that shape *how* thinking happens rather than *what* is analyzed. See individual `SKILL.md` files for full methodology.

### Archaeology — Layer Subsets

Full excavation runs all 12 layers in sequence. For targeted analysis, select specific layers:

| Need | Layers | Effect |
|------|--------|--------|
| Assumption check | `F2` | Surface unconscious constraints |
| Perspective shift | `F3, F6, F8` | Zoom, oscillate, scale-shift |
| Tension mapping | `F2, F7, F9` | Assumptions, tensions, intuition |
| Design review | `F4, F10, F11` | Structure, autonomy, production assessment |
| Something feels off | `F9` | Intuitive sensing — best after other layers have cleared the ground |

### Triad — Lens Selection

Default 4 lenses (integration, transcendence, context-dependence, meta-perspective) are sufficient for most uses. Extended lenses add depth when a tension is central to a decision.

| Situation | Lenses |
|-----------|--------|
| Quick orientation | Default 4 |
| Architectural decision | Default 4 + Emergence + Negation |
| Creative exploration | Oscillation + Transformation + Dissolution |
| Stress-testing a choice | Meta-Perspective + Negation + Dissolution |
| Recurring tension worth thorough exploration | All 11 |

### Dialogue Mode

Three cognitive skills support `--dialogue` for collaborative inquiry instead of one-shot delivery:

| Skill | Pauses at | You steer |
|-------|-----------|-----------|
| `/archaeology` | Every 2-3 layers | Which layers to explore deeper, what resonates |
| `/triad` | After first 2 lenses | Whether to reframe the polarity, which lenses to add |
| `/cognitive-debug` | After trace + breakpoints | Confirm or correct the trace before corrective path |

**Use dialogue** when the subject is personal or ambiguous — you hold context that isn't in the documents, and your input mid-stream changes quality of output. **Use one-shot** when the subject is well-documented and Claude can reason autonomously. Dialogue mode is not compatible with `/compose`.

### Quick Checks

| Situation | Run |
|-----------|-----|
| Am I missing something? | `/reframe --searches negative` |
| Is this the right problem? | `/archaeology --layers F2,F7` |
| What are we assuming? | `/archaeology --layers F2` |
| What if the opposite? | `/inversion` |
| What's good about what we have? | `/steelman` |
| What can an attacker do? | `/threat-model` |
| Are we ready to deploy? | `/launch-gate` |
| What breaks in production? | `/compose ghost, incident-ready` |
| Are these identifiers earning their keep? | `/garden greenfield` |

## Environment Contract

Skills that "read all project markdown documents" expect a specific documentation architecture. When present, output is grounded and specific. When absent, skills still work but produce more generic findings.

| Document | Skills use it for | Without it |
|----------|------------------|------------|
| `CONTEXT.md` | Purpose, constraints, stakeholders | Analysis happens in a vacuum |
| `DESIGN.md` | Architecture, patterns, decisions | Architecture-dependent skills lose grounding |
| `DECISIONS.md` | ADRs and rationale | Can't reference prior decisions |
| `ROADMAP.md` | Phases, milestones, status | Phase-aware skills can't map to timeline |
| `CLAUDE.md` | AI-specific project context | Skills miss project conventions |

**Minimum viable:** CONTEXT.md + DESIGN.md. **Full environment:** All five + codebase.

## Stage Map

| Stage | Primary skills |
|-------|---------------|
| Exploring / deciding | archaeology, triad, reframe, consequences |
| Designing | scope, gaps, deep-review, api-review |
| Pre-implementation | steelman, inversion, threat-model, implement |
| Implementing | context-switch, tomorrow, ghost |
| Post-implementation | verify, drift-detect, coherence |
| Pre-launch | launch-gate, hardening-audit, ops-review, incident-ready |
| Maintaining | drift-detect, garden, supply-chain-audit, doc-health |

## Principles

- **Skills are lenses** — each examines from a different angle. **Commands are workflows** — orchestrated sequences.
- **All skills are read-only** — they propose changes but never modify files.
- **Action-biased** — every finding includes what, where, and the specific fix.
- **Composable** — `/compose` chains skills with threaded context. Order and combination matter.
- **Architecture-derived** — security and readiness skills reason from the specific stack, not generic checklists.
- **Every word in a skill prompt shapes the cognitive field** — skill definitions are precision instruments. Do not paraphrase.
- **One-shot by default, dialogue on request** — cognitive skills support `--dialogue` for collaborative inquiry.
