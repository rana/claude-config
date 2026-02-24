# Skill System — Operational Doctrine

How to wield the full skill system as a coherent practice. COGNITIVE-GUIDE.md is the deep playbook for the 4 cognitive steering skills. This document maps the whole system — taxonomy, selection, lifecycle, composition, and environment.

## Taxonomy

28 skills in 6 families. The families aren't rigid categories — skills cross boundaries. But knowing the family helps you find what you need.

### Pre-Implementation (size the work before doing it)

| Skill | One-line | When to reach for it |
|-------|----------|---------------------|
| `/scope` | Surface area + dependency chain + minimum viable version | Before committing to any change |
| `/consequences` | Forward-propagate 2nd and 3rd order effects | Before committing to a significant decision |
| `/steelman` | Best case for the status quo before proposing change | When questioning an existing decision |
| `/inversion` | Flip every assumption, see what's load-bearing vs habitual | When stress-testing a design or exploring alternatives |

**Family logic:** These skills protect you from premature commitment. Run them *before* you start building. `/scope` sizes the work. `/consequences` maps the ripple effects. `/steelman` prevents premature abandonment. `/inversion` prevents habitual thinking.

### Quality Gates (review what exists)

| Skill | One-line | When to reach for it |
|-------|----------|---------------------|
| `/deep-review` | Multi-dimensional quality gate: coherence, gaps, errors, architecture | At phase boundaries or before implementation begins |
| `/coherence` | Cross-document consistency and reference integrity | After significant document changes |
| `/gaps` | Systematic search for omissions and blind spots | When preparing for implementation or asking "what am I not seeing?" |
| `/api-review` | API surface consistency and design patterns | When reviewing endpoints, data models, or naming conventions |
| `/docs-quality` | Documentation practice evaluation for AI + human readers | When evaluating whether docs serve their audiences |

**Family logic:** These skills examine artifacts that already exist. `/deep-review` is the comprehensive gate — it subsumes coherence, gaps, and errors in a single pass. Use the specialized skills (`/coherence`, `/gaps`, `/api-review`) when you need depth in one dimension rather than breadth across all.

**Selection heuristic:** If you only run one quality skill, run `/deep-review`. If deep-review surfaces a cluster of findings in one dimension, follow up with the specialized skill for that dimension.

### Production & Security (ready to ship?)

| Skill | One-line | When to reach for it |
|-------|----------|---------------------|
| `/threat-model` | STRIDE-based threat identification from actual architecture | Before implementation, at phase boundaries, when attack surface changes |
| `/hardening-audit` | Production hardening checklist derived from the specific stack | Before deployment, after adding external integrations |
| `/ghost` | Hidden dependencies and implicit assumptions | When asking "what breaks at 2am?" |
| `/launch-gate` | Go/no-go checklist across 11 readiness dimensions | When asking "are we ready to ship this phase?" |
| `/ops-review` | Deployment, costs, monitoring, incident response, scaling | Before launch or when evaluating infrastructure |
| `/incident-ready` | Runbook coverage, escalation paths, communication templates | When transitioning from development to production |
| `/supply-chain-audit` | Dependency risk, license compliance, vendor SLAs | Periodically, before major version bumps, or when evaluating new dependencies |

**Family logic:** These skills form a security and operations pipeline. They have a natural ordering: `/threat-model` → `/hardening-audit` → `/ghost` → `/launch-gate`. Each narrows the aperture. Threat-model maps the attack surface. Hardening-audit checks specific technical controls. Ghost finds what both missed (the implicit stuff). Launch-gate makes the go/no-go call.

**The operations sub-chain:** `/ops-review` → `/incident-ready` → `/launch-gate`. Operations readiness, then incident response readiness, then the comprehensive gate.

### Cognitive Steering (shape how thinking happens)

| Skill | One-line | When to reach for it |
|-------|----------|---------------------|
| `/archaeology` | 12-layer excavation from surface through meta-cognition | Before significant decisions, when something feels off |
| `/triad` | Dimensional tension analysis — hold polarities, don't collapse them | Any "X or Y?" decision |
| `/reframe` | Geometric spatial search: negative, adjacent, orthogonal, parallel | When conventional analysis produces nothing but something's still missing |
| `/cognitive-debug` | Trace reasoning back to where it broke | When a conclusion doesn't feel right |

**Family logic:** These skills change what you can see, not what you look at. See COGNITIVE-GUIDE.md for the full playbook — it covers these 4 skills in depth with dialogue mode, layer subsets, lens selection, and composition patterns.

### Maintenance & Lifecycle (keep the system healthy)

| Skill | One-line | When to reach for it |
|-------|----------|---------------------|
| `/drift-detect` | Compare stated architecture against emergent code patterns | Periodically, or when the codebase feels inconsistent |
| `/coherence` | Cross-document consistency check | After significant document changes |
| `/garden` | Identifier lifecycle — prune, merge, reorder, audit | When identifier systems accumulate weight |
| `/tomorrow` | Capture what future-you needs to know while context is fresh | After implementation, after discovering something non-obvious |

**Family logic:** These skills fight entropy. Code drifts from its stated architecture (`/drift-detect`). Documents drift from each other (`/coherence`). Identifier systems accumulate weight (`/garden`). Context evaporates (`/tomorrow`). Run these periodically, not just at milestones.

### Orientation & Workflow (navigate and process)

| Skill | One-line | When to reach for it |
|-------|----------|---------------------|
| `/context-switch` | 60-second briefing on a subsystem's current state | When switching between tasks |
| `/workflow-trace` | Trace an end-to-end workflow for friction and missing steps | When evaluating user journeys or developer workflows |
| `/why-chain` | Recursive "why?" until you hit bedrock constraint or arbitrary choice | When understanding why code or decisions exist |
| `/scratch` | Process the idea backlog, route items to appropriate skills | When reviewing what to work on next |

**Family logic:** These skills help you navigate. `/context-switch` reorients you. `/workflow-trace` maps processes end-to-end. `/why-chain` traces decisions to their foundations. `/scratch` routes unprocessed ideas to the right skill.

## Selection: Which Skill When?

When you face a situation and aren't sure which skill to use, work through this:

**1. What's the nature of the question?**

| You're asking... | Start with |
|-----------------|------------|
| "How big is this change?" | `/scope` |
| "What happens if we do this?" | `/consequences` |
| "Should we change this?" | `/steelman` first, then `/inversion` |
| "What are we missing?" | `/gaps` (concrete) or `/reframe` (perceptual) |
| "Is this ready?" | `/deep-review` (quality) or `/launch-gate` (production) |
| "Is this secure?" | `/threat-model` → `/hardening-audit` |
| "What would break?" | `/ghost` |
| "Why does this exist?" | `/why-chain` |
| "What's going on here?" | `/context-switch` |
| "This feels wrong but I can't say why" | `/archaeology --layers F9` or `/cognitive-debug` |
| "X or Y?" | `/triad` |
| "What aren't we seeing?" | `/reframe` |
| "Are the docs consistent?" | `/coherence` |
| "Is this over-engineered?" | `/crystallize` |

**2. What stage are you at?**

| Project stage | Primary skills | Why |
|--------------|---------------|-----|
| **Exploring/deciding** | archaeology, triad, reframe, consequences | Shape perception before committing |
| **Designing** | scope, gaps, deep-review, api-review | Size the work, find omissions, gate quality |
| **Pre-implementation** | steelman, inversion, threat-model | Stress-test decisions before building |
| **Implementing** | context-switch, tomorrow, ghost | Navigate, capture knowledge, surface implicit deps |
| **Reviewing** | deep-review, coherence, drift-detect | Quality gate, consistency, architectural fidelity |
| **Pre-launch** | launch-gate, hardening-audit, ops-review, incident-ready | Production readiness across all dimensions |
| **Maintaining** | drift-detect, garden, coherence, supply-chain-audit | Fight entropy, manage lifecycle |

## Composition Patterns

Skills compose. The `/compose` command chains skills in sequence, threading context forward — each subsequent skill sees what previous passes discovered. Patterns beyond what COGNITIVE-GUIDE.md covers:

### The Analytical Pipeline

```bash
# Size → propagate → gate
/compose scope, consequences, deep-review : "the proposed change"
```

**When:** You have a change request and need to go from "what is it?" to "should we do it?" in one pass. Scope maps the surface area, consequences propagates effects, deep-review gates quality of the analysis.

### The Stress Test

```bash
# Defend → attack → find what survives
/compose steelman, inversion, gaps : "the current architecture"
```

**When:** You're questioning whether to change something significant. Steelman builds the best case for keeping it. Inversion flips assumptions. Gaps finds what neither perspective addressed.

### The Security Sweep

```bash
# Systematic → technical → hidden → readiness
/compose threat-model, hardening-audit, ghost : "the system"
```

**When:** Comprehensive security review. Threat-model maps the attack surface systematically. Hardening-audit checks specific technical controls. Ghost finds the implicit dependencies both missed.

### The Entropy Audit

```bash
# Architecture → documents → identifiers
/compose drift-detect, coherence, garden : "the project"
```

**When:** Periodic health check. Drift-detect compares stated vs. actual architecture. Coherence checks document consistency. Garden audits identifier lifecycle. Run quarterly or when things feel inconsistent.

### The Decision Pipeline

```bash
# Explore → tension → forward-propagate → simplify
/compose archaeology, triad, consequences, crystallize : "the decision"
```

**When:** Major decision that justifies thorough analysis. Archaeology excavates the decision space. Triad maps the core tension. Consequences propagates the preferred direction. Crystallize cuts to the essential.

### The Production Pipeline

```bash
# Operations → incidents → cost → go/no-go
/compose ops-review, incident-ready, launch-gate : "Phase N"
```

**When:** Pre-launch readiness check. Each skill narrows the aperture from broad operational readiness to incident-specific preparedness to the comprehensive gate.

### The Knowledge Capture

```bash
# Trace decisions → capture context → surface hidden knowledge
/compose why-chain, tomorrow, ghost : "the module we just built"
```

**When:** Post-implementation. Before context evaporates, trace why decisions were made, capture what future-you needs to know, and surface what's implicit.

### The Perception Shift

```bash
# Debug the stuck point → see new angles → excavate what emerges
/compose cognitive-debug, reframe, archaeology --layers F9 : "the stuck point"
```

**When:** Analysis has stalled. Cognitive-debug finds where thinking broke. Reframe opens new spatial dimensions. Archaeology F9 (intuitive sensing) captures what wants to emerge after the clearing.

### The Newcomer Audit

```bash
# Trace the workflow → find friction → assess documentation
/compose workflow-trace, gaps, docs-quality : "new developer onboarding"
```

**When:** Evaluating whether someone new can navigate the project. Workflow-trace maps the actual journey. Gaps finds what's missing. Docs-quality assesses whether documentation serves its audiences.

## Composition Principles

**Order matters.** Skills that expand perception (archaeology, reframe) should run before skills that analyze specifics (gaps, threat-model, coherence). Skills that simplify (crystallize) should run last.

**Three is the sweet spot.** Two skills is a focused pair. Three is a productive pipeline. Four or more risks context dilution — each skill sees less of what matters because it's processing more from previous passes.

**Threading vs. independent runs.** Compose threads context — each skill accounts for previous findings. If you want independent perspectives, run skills separately. `/compose steelman, inversion` gives you steelman-informed inversion. Running `/steelman` then `/inversion` separately gives you two independent views.

**Not everything composes.** `/context-switch` is a navigation tool, not an analysis lens — it doesn't produce findings to thread forward. `/scratch` is a router, not a composable skill. `/calibrate` sets session parameters, not analysis context.

**Dialogue mode is incompatible with compose.** Compose needs autonomous passes. Use dialogue for standalone deep dives where your mid-stream input changes the quality of output.

## Environment Contract

Skills that "read all project markdown documents" expect a specific documentation architecture. When these documents exist, skills produce grounded, specific output. When they don't, skills still work but produce more generic findings.

| Document | What skills use it for | Impact of absence |
|----------|----------------------|-------------------|
| `CONTEXT.md` | Project purpose, constraints, stakeholders | Skills analyze in a vacuum without project context |
| `DESIGN.md` | Architecture, patterns, technical decisions | Architecture-dependent skills (drift-detect, api-review) lose grounding |
| `DECISIONS.md` | ADRs and their rationale | Skills can't reference prior decisions; steelman and why-chain lose source material |
| `ROADMAP.md` | Phases, milestones, what's done vs. planned | Phase-dependent skills (launch-gate, scope) can't map to implementation timeline |
| `CLAUDE.md` | AI-specific project context and conventions | Skills work without it, but miss project-specific conventions |

**Minimum viable environment:** CONTEXT.md + DESIGN.md. These give skills enough grounding for useful output.

**Full environment:** All five documents plus a codebase to examine. This is what skills assume when they say "read all project markdown documents and examine the codebase."

**No documents at all:** Skills still run, but shift to codebase-only analysis. Output is less connected to intent and more connected to what the code actually does.

## Relationship to Other Documents

| Document | What it is | Audience |
|----------|-----------|----------|
| SKILL-SYSTEM.md (this) | Operational doctrine for the full 28-skill system | Someone who has the skills and wants to use them effectively |
| COGNITIVE-GUIDE.md | Deep playbook for the 4 cognitive steering skills | Someone who wants to understand and wield the cognitive skills specifically |
| Individual SKILL.md files | Self-contained skill definitions | Claude — these are the actual prompts that execute |

COGNITIVE-GUIDE.md goes deeper on 4 skills. This document goes wider across all 28. They reference each other but don't duplicate.

## Team Adoption

If you're sharing these skills with a team:

**Start with 5, not 28.** Recommended starter set: `/scope`, `/deep-review`, `/gaps`, `/threat-model`, `/crystallize`. These cover the highest-value activities (sizing, quality gating, omission detection, security, simplification) without requiring the cognitive steering philosophy.

**Add cognitive skills for leads.** `/archaeology` and `/triad` are most valuable for people making architectural decisions. They require understanding the cognitive model — point them to COGNITIVE-GUIDE.md.

**Compose recipes are the team playbook.** Don't teach individual skills — teach patterns. "Before any significant decision, run `/compose steelman, inversion, consequences`" is more actionable than explaining 3 skills independently.

**The environment contract is mandatory for teams.** Skills that expect CONTEXT.md and DESIGN.md produce inconsistent results if some team members have those documents and others don't. Agree on the documentation architecture before rolling out the skills.
