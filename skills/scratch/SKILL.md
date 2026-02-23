---
name: scratch
description: Process scratch.md backlog. Surfaces unhandled items, identifies which analysis skills to apply, and proposes next actions. Use to review your idea backlog and decide what to work on.
disable-model-invocation: true
argument-hint: "[item number, 'batch', or 'summary']"
---

Read `scratch.md` in the project root.

## Scratch Pad Processor

### Parse

1. **Identify all items** — Items are separated by `---` dividers or appear as numbered entries in lists. Items may also appear as `- [ ]` task items.
2. **Check status** — Items marked with `✅`, `[x]`, or `done` are completed. Items marked `[P1]`, `[P2]`, `[P3]` have explicit priority. Everything else is open.
3. **Ignore** — The frontmatter block and any template/format explanation sections.

### Classify

For each open item, identify the best analysis skill:

| Pattern in item | Suggested skill |
|----------------|-----------------|
| Coherence, cross-reference, alignment, consistency | `/coherence` |
| Gap, omission, blind spot, missing, "what am I not asking" | `/gaps` |
| Simplify, remove, crystalline, over-engineered | `/crystallize` |
| API, endpoint, REST, data model, schema | `/api-review` |
| Operational, deployment, cost, monitoring, scaling | `/ops-review` |
| Documentation, docs, onboarding, staleness | `/docs-quality` |
| Workflow, user journey, persona, trace through | `/workflow-trace` |
| Ripple effect, impact, "what happens if", consequences | `/consequences` |
| Hidden, implicit, assumption, undocumented, environment | `/ghost` |
| Size, scope, "how big", impact, touches, minimum viable | `/scope` |
| Architecture, drift, evolved, inconsistent patterns | `/drift-detect` |
| Defend, keep, status quo, "what's good about" | `/steelman` |
| Invert, opposite, flip, "what if not", stress-test | `/inversion` |
| Future, confuse, remember, dragons, workaround, magic | `/tomorrow` |
| Why, root cause, reason, origin, archaeology | `/why-chain` |
| Mission, principle, fidelity, DELTA, calm technology | `/mission-align` (if available) |
| Cultural, perspective, sensitivity, language, i18n | `/cultural-lens` (if available) |
| Reading, seeker, UX, experience, accessibility | `/seeker-ux` (if available) |
| Comprehensive, multi-dimensional, deep review | `/deep-review` |
| Open-ended, novel, exploratory, "what wants to emerge" | `/explore-act` |

### Present

**If no argument provided:** Show a summary table of all open items with:
- Item number or position
- One-line summary
- Priority (P1/P2/P3 or inferred)
- Recommended skill
- Whether it's better suited for interactive (skill) or autonomous (Elmer)

**If argument is an item number:** Show the full item text, recommended skill, and rationale. Ask if the user wants to proceed.

**If argument is `batch`:** Generate an Elmer-compatible topic list from all open items, grouped by recommended archetype. Present for review.

**If argument is `summary`:** Show counts: total items, completed, open, by priority, by recommended skill.

## Output Management

**Hard constraints:**
- For the summary table, show at most 15 items per page. Offer to continue if more exist.
- Write findings incrementally. Do not accumulate a single large response.

**If output would exceed comfortable length:**
Stop. Deliver items processed so far. State how many remain and offer to continue.
