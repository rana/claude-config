# Claude Code Skills & Commands Reference

Personal toolkit for design analysis, workflow automation, cognitive steering, and thinking amplification.

## Quick Reference

| Command | What it does | When to use |
|---------|-------------|-------------|
| `/explore` | Deep multi-dimensional perspective | Open-ended investigation |
| `/explore-act` | Same, biased toward action | Investigation that should produce a change list |
| `/calibrate` | Set session thinking parameters | Start of session, mode shift |
| `/commit-message` | Draft a commit message | Before committing, want to review message first |
| `/commit-sync` | Stage, commit, push | Have a message ready, want to execute |
| `/commit-all` | Draft message + stage + commit + push | End-to-end commit workflow |
| `/park` | Save work state + context notes | Stopping work, switching tasks, end of day |
| `/resume` | Restore parked work context | Starting work, returning to a task |
| `/morning` | Daily development briefing | Beginning of session |
| `/compose` | Chain multiple skills in sequence | Need multi-dimensional analysis in one pass |

## Skills by Category

### Analysis Lenses

Each skill looks at a design from a different angle. Use them individually or chain via `/compose`.

| Skill | Lens | Trigger phrases |
|-------|------|----------------|
| `/coherence` | Cross-document consistency, identifier integrity, stated vs. actual state | "Do the docs agree?" "Is this consistent?" |
| `/gaps` | Missing decisions, blind spots, unaddressed scenarios, spatial gaps | "What am I not seeing?" "What's missing?" |
| `/crystallize` | Simplification, editorial sharpening, removing dead weight | "This feels heavy." "Can we simplify?" |
| `/api-review` | API surface, data model, naming, pagination, versioning | "Review the API." "Check the endpoints." |
| `/ops-review` | Deployment, costs, monitoring, incident response, scaling | "Are we ready to launch?" "Check ops." |
| `/docs-quality` | Documentation as communication architecture | "Are the docs good enough?" |
| `/deep-review` | All dimensions combined — the comprehensive quality gate | "Full review before implementation." |
| `/workflow-trace` | End-to-end workflow mapping, friction points, handoffs | "Trace the user journey." "Walk through the flow." |
| `/scratch` | Process scratch.md backlog, classify items, route to skills | "What's in the backlog?" "Triage scratch." |

### Forward-Looking / Causal

| Skill | Lens | Trigger phrases |
|-------|------|----------------|
| `/consequences` | 2nd and 3rd order effects of a proposed change | "What happens if we do this?" "Ripple effects?" |
| `/scope` | Pre-implementation sizing and impact mapping | "How big is this?" "What does this touch?" |
| `/drift-detect` | Has the code drifted from stated architecture? | "Are we still following the design?" |

### Hidden Structure

| Skill | Lens | Trigger phrases |
|-------|------|----------------|
| `/ghost` | Invisible dependencies, undocumented assumptions | "What breaks at 2am?" "Hidden assumptions?" |
| `/why-chain` | Root cause archaeology — recursive "why?" | "Why is it this way?" "What's the root reason?" |

### Thinking Amplifiers

| Skill | Lens | Trigger phrases |
|-------|------|----------------|
| `/steelman` | Strongest defense of the current approach before proposing changes | "What's good about the status quo?" |
| `/inversion` | Systematic assumption flipping for stress-testing | "What if the opposite were true?" |
| `/tomorrow` | Future-self documentation — what will confuse you later? | "Will this make sense in 6 months?" |

### Cognitive Steering

Skills that shape *how* thinking happens rather than *what* is analyzed. See [COGNITIVE-GUIDE.md](COGNITIVE-GUIDE.md) for in-depth usage.

| Skill | Lens | Trigger phrases |
|-------|------|----------------|
| `/archaeology` | 12-layer cognitive excavation — assumptions, tensions, meta-cognition | "Dig deep." "Full archaeology on this." |
| `/triad` | Dimensional tension analysis through synthesis lenses | "X vs Y" "Explore this tension." |
| `/reframe` | Geometric spatial search — negative, adjacent, orthogonal, parallel | "Reframe this." "What am I not seeing?" |
| `/cognitive-debug` | Reasoning trace and correction — breakpoints in thought | "Where did my thinking go wrong?" |

### Context & Continuity

| Skill | Lens | Trigger phrases |
|-------|------|----------------|
| `/context-switch` | Rapid reorientation to a different codebase area | "Bring me up to speed on [area]." |
| `/park` | Capture work state + mental context for later | "I need to stop." "Save my place." |
| `/resume` | Restore parked context and present briefing | "Where was I?" "What was I doing?" |
| `/morning` | Session-start briefing: branches, PRs, recent changes | "What's going on?" "Catch me up." |

## Typical Workflows

### Starting a new feature
1. `/scope` — How big is this? What does it touch?
2. `/gaps` — What's missing from the requirements?
3. `/consequences` — What are the ripple effects?
4. Implement
5. `/deep-review` — Quality gate before merge

### Deep exploration of a design decision
1. `/archaeology "should we use X approach"` — Full cognitive excavation
2. `/triad "X vs Y"` — Dimensional tension analysis of the core polarity
3. `/consequences` — Forward-propagation of the preferred direction
4. `/crystallize` — Strip to essential structure

### Returning to work
1. `/morning` or `/resume` — Restore context
2. Check todo list — Pick up where you left off

### Reviewing a design
1. `/deep-review` — Comprehensive first pass
2. `/steelman` — What's working well about this?
3. `/crystallize` — What can be simplified?
4. `/consequences` — If we ship this, what happens next?

### When thinking feels stuck
1. `/reframe "the problem"` — Spatial search for new angles
2. `/inversion` — Flip assumptions, see what holds
3. `/archaeology --layers F2,F7,F9` — Targeted: assumptions, tensions, intuition
4. `/cognitive-debug` — If a conclusion feels wrong, trace back to the breakpoint

### Investigating unfamiliar code
1. `/context-switch [area]` — Get oriented
2. `/why-chain` — Understand the reasoning
3. `/ghost` — Surface hidden dependencies
4. `/drift-detect` — Is this area still aligned with the architecture?

### Pre-launch
1. `/ops-review` — Operational readiness
2. `/ghost` — Hidden dependencies that could break in production
3. `/api-review` — Surface consistency
4. `/docs-quality` — Can the next person understand this?

### Navigating a strategic tension
1. `/triad "performance vs maintainability"` — Map the tension through multiple lenses
2. `/steelman` each side — What's the strongest case for each pole?
3. `/reframe` — What spatial searches reveal about the decision space
4. `/consequences` — Forward-propagate each direction

### Stopping work
1. `/park` — Save context and next steps

## Design Philosophy

- **Skills are lenses** — each examines a design from a different angle
- **Commands are workflows** — orchestrated sequences of actions
- **All skills are read-only** — they propose changes but never modify files
- **Action-biased** — every finding comes with a specific proposed change
- **Composable** — use `/compose` to chain skills into multi-pass analysis
- **Every word shapes the cognitive field** — skill prompts are precision instruments, not instructions to paraphrase
