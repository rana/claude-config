# Cognitive Skills — Usage Guide

How to use the cognitive steering skills effectively. SKILLS.md is the reference (what exists). This is the playbook (how to think about using them). SYSTEM.md is the architecture they live inside.

## What These Skills Are

The analytical skills (`/coherence`, `/gaps`, `/ops-review`, etc.) examine *what* exists in a design. The cognitive skills shape *how* thinking happens — they steer the AI's cognitive orientation before and during analysis.

This distinction matters. Running `/gaps` finds missing things. Running `/archaeology` before `/gaps` changes what kinds of missing things become visible — it surfaces assumptions you didn't know you were making, which reframes what counts as a gap.

The cognitive skills were distilled from extended research into how language shapes AI processing. Key findings:

- **Geometric metaphors** (negative space, orthogonal, gradient) map naturally to transformer architecture and produce more precise cognitive steering than abstract descriptors
- **Sequenced prompts** build cognitive momentum — each layer prepares the ground for the next, like an archaeological dig
- **Dimensional tensions** (X vs Y) analyzed through multiple synthesis lenses produce richer insight than binary evaluation
- **Reasoning traces** can be debugged like code — with breakpoints, corrective questions, and re-execution

## The Four Cognitive Skills

### `/archaeology` — Layered Cognitive Excavation

The comprehensive tool. Twelve layers that build from surface inquiry through assumptions, perspectives, tensions, meta-cognition, and intuition to a synthesis.

**The sequence matters.** F1 (Opening Inquiry) surfaces initial questions. F2 (Unconscious Patterns) reveals hidden assumptions. F3 (Resolution & Perspective) shifts the viewing angle. Each layer prepares the ground for what follows — by F9 (Intuitive Sensing), you've cleared enough cognitive brush to hear signals that F1 would have missed entirely.

```
/archaeology "our approach to error handling across the API"
/archaeology "whether this project needs a database" --layers F2,F7,F9
/archaeology "the team's deployment process" --relational
```

**Layer subsets for common needs:**

| Need | Layers | What it does |
|------|--------|-------------|
| Quick assumption check | `F2` | Surface unconscious constraints |
| Perspective shift | `F3, F6, F8` | Zoom, oscillate, scale-shift |
| Tension mapping | `F2, F7, F9` | Assumptions → tensions → intuition |
| Design review | `F4, F10, F11` | Structure → autonomy → production assessment |
| Full excavation | All (default) | The complete 12-layer sequence |

**When to use:**
- Before making a significant decision — run the full sequence
- When discussion has stalled — run F3 + F6 (perspective and dynamic understanding)
- When something feels off but you can't articulate it — run F9 (intuitive sensing)
- After implementation, before merge — run F11 (production assessment)

### `/triad` — Dimensional Tension Analysis

Given a polarity (X vs Y), analyze it through synthesis lenses that create genuine intellectual tension in three directions rather than flat compromise.

The default four lenses are sufficient for most uses:
- **Integration**: How do X and Y work together?
- **Transcendence**: What emerges beyond both?
- **Context-Dependence**: When is X better? When Y?
- **Meta-Perspective**: What assumptions do both share?

The extended lenses (Emergence, Oscillation, Interference, Transformation, Recursion, Negation, Dissolution) add depth when a tension is central to a decision and worth thorough exploration.

```
/triad "monolith vs microservices"
/triad "type safety vs development speed" --lenses integration,context-dependence,negation
/triad "consistency vs availability in our data layer" --all-lenses
```

**When to use:**
- Any "X or Y?" decision — reframe it as a tension to understand rather than a choice to make
- Architecture decisions where both approaches have legitimate strengths
- When a team is polarized — the lenses create shared vocabulary for the tension
- Strategic planning — map the core tensions the project lives within

**Lens selection guidance:**

| Situation | Recommended lenses |
|-----------|-------------------|
| Quick orientation | Default 4 |
| Architectural decision | Default 4 + Emergence + Negation |
| Creative exploration | Oscillation + Transformation + Dissolution |
| Stress-testing a choice | Meta-Perspective + Negation + Dissolution |
| Understanding a recurring tension | All 11 |

### `/reframe` — Geometric Spatial Search

Apply four spatial search patterns to see what conventional analysis misses:

- **Negative space**: What's conspicuously absent? The voids and patterns of absence.
- **Adjacent space**: What's one step away? Neighboring possibilities.
- **Orthogonal space**: What's perpendicular to current trajectory? Radical reframings.
- **Parallel space**: What analogous patterns exist elsewhere? Cross-domain mapping.

```
/reframe "our authentication architecture"
/reframe "the onboarding flow" --searches negative,orthogonal
/reframe "why users aren't adopting feature X"
```

**When to use:**
- When `/gaps` finds nothing but something still feels missing — try negative space
- When incremental improvements aren't enough — try orthogonal space
- When you want inspiration from other domains — try parallel space
- When you need to find low-hanging fruit — try adjacent space

### `/cognitive-debug` — Reasoning Trace and Correction

When a conclusion feels wrong or a decision led somewhere unexpected, trace the reasoning back to find where it broke.

```
/cognitive-debug "we concluded the API needs rate limiting but now I'm not sure"
/cognitive-debug "Claude suggested X pattern but it doesn't fit our codebase"
/cognitive-debug "the team decided on microservices but it's causing more problems"
```

**Common breakpoints it identifies:**
- **Fear-driven reasoning**: Solving problems that don't exist because they *might*
- **Premature compression**: "X means Y" without checking
- **Pattern over mechanism**: "This looks like that other thing" when it isn't
- **Coherence drive**: Picking an answer to avoid ambiguity
- **Associative momentum**: Following a line of thought past its usefulness

**When to use:**
- After a decision that led to unexpected consequences — trace back to find where
- When Claude (or you) reached a conclusion that doesn't feel right
- During code review when you can't articulate why something seems off
- As a learning tool — understand your own reasoning patterns

## Dialogue Mode

Three cognitive skills support `--dialogue` for collaborative inquiry instead of one-shot delivery:

```
/archaeology "our data model" --dialogue
/triad "performance vs correctness" --dialogue
/cognitive-debug "the decision to use event sourcing" --dialogue
```

**What changes:** The skill pauses at natural breakpoints and asks questions before proceeding. Your answers steer the remaining analysis.

| Skill | Pause points | What the user steers |
|-------|-------------|---------------------|
| `/archaeology` | Every 2-3 layers | Which layers to explore deeper, what resonates |
| `/triad` | After first 2 lenses | Whether to reframe the polarity, which lenses to add |
| `/cognitive-debug` | After trace + breakpoints (Steps 1-3) | Confirm or correct the trace before corrective path |

**When to use dialogue vs. one-shot:**

- **Dialogue** when the subject is personal or ambiguous — when you know something the tool doesn't, and your input mid-stream changes the quality of output. Archaeology of a decision you made. Debugging reasoning you were part of. Tensions where you hold context that isn't in the documents.
- **One-shot** when the subject is well-documented and the tool can reason autonomously. Code architecture review. Security analysis. Gap detection against a spec.

**Dialogue mode is not compatible with `/compose`** — compose chains need autonomous passes. Use dialogue for standalone deep dives.

## Multi-Skill Workflows

### The Explore-then-Analyze Pattern

Use cognitive skills first to shape perception, then analytical skills to examine specifics.

```
/compose archaeology, gaps : error handling
```

This runs `/archaeology` on error handling (surfaces assumptions, tensions, hidden structure), then runs `/gaps` with the archaeology findings as context. The gaps analysis sees deeper because the archaeology shifted what counts as visible.

### The Tension-then-Consequence Pattern

```
/compose triad, consequences : "server-side rendering vs client-side rendering"
```

Map the tension through multiple lenses, then forward-propagate the implications of the preferred direction.

### The Debug-then-Reframe Pattern

When stuck after a wrong turn:

```
/cognitive-debug "our caching strategy"
# ... identifies the breakpoint ...
/reframe "caching in our architecture"
# ... finds new angles the original reasoning missed ...
```

### The Full Strategic Analysis

For major decisions that justify thorough exploration:

```
# 1. Excavate the decision space
/archaeology "whether to rewrite the billing system"

# 2. Map the core tension
/triad "rewrite vs incremental refactor"

# 3. Steelman the status quo
/steelman "the current billing system"

# 4. Search spatial dimensions
/reframe "billing system architecture"

# 5. Forward-propagate the preferred direction
/consequences "rewriting billing as a separate service"

# 6. Crystallize to essential decision
/crystallize
```

Or as a compose chain for the core of it:

```
/compose archaeology, triad, consequences : billing system rewrite
```

### Lightweight Cognitive Checks

Not every situation needs the full toolkit. Quick single-skill invocations:

| Situation | Quick check |
|-----------|------------|
| "Am I missing something?" | `/reframe --searches negative` |
| "Is this the right problem?" | `/archaeology --layers F2,F7` |
| "Should we use X or Y?" | `/triad "X vs Y"` |
| "Why did that reasoning fail?" | `/cognitive-debug` |
| "What are we assuming?" | `/archaeology --layers F2` |
| "What would happen if we did the opposite?" | `/inversion` |
| "What's the strongest case for what we have?" | `/steelman` |
| "What can an attacker do here?" | `/threat-model` |
| "Are we ready to deploy?" | `/launch-gate` |
| "What breaks when this hits production?" | `/compose ghost, incident-ready` |
| "Are these ADRs earning their keep?" | `/garden greenfield` |

## Integration with Elmer

The cognitive skills work in Claude Code sessions (interactive). Elmer works autonomously on branches. They complement each other:

| Situation | Tool | Why |
|-----------|------|-----|
| Deep exploration of a tension | `/triad` in Claude Code | Interactive, you steer the lenses |
| Overnight archaeological survey of 10 areas | `elmer batch` with archaeology topics | Autonomous, parallel, persistent |
| Quick reframe during coding | `/reframe` in Claude Code | Immediate, conversational |
| Systematic cognitive debug of past decisions | `elmer explore "cognitive-debug: our auth decision"` | Background, thorough |

Elmer topic files can reference cognitive skills:

```markdown
# .elmer/explore-act.md

---

Apply /archaeology to our payment processing pipeline.
Focus on layers F2 (unconscious patterns), F7 (tensions),
and F11 (production assessment).

---

Apply /triad to "synchronous vs asynchronous payment processing"
with all 11 lenses.

---
```

## The `/calibrate` Command

Use at session start to set thinking parameters:

```
/calibrate
/calibrate "bold speculation, generative mode, high-level resolution"
/calibrate "production mode, detail resolution, conservative"
/calibrate "crystalline craft, exploratory, bold"
```

This establishes session defaults for directness, resolution, thinking mode, speculation tolerance, craft level, and output shape. It's the cognitive equivalent of setting your IDE preferences before starting work.

**Parameters:**
- **Directness** — how directly to lead with strongest thoughts
- **Resolution** — high-level / mid-level / detail / adaptive
- **Thinking Mode** — exploratory / analytical / generative / production
- **Speculation Tolerance** — conservative / moderate / bold
- **Craft** — functional / composed / crystalline (how much attention to quality of expression)
- **Output Shape** — dense / structured / conversational

**Pairs well with:**
- `/morning` — Calibrate, then get the morning briefing
- `/resume` — Restore context, then calibrate for the work ahead

## The `/scratch` Router

The scratch skill now routes cognitive items too:

| Pattern in scratch item | Suggested skill |
|------------------------|-----------------|
| "tension", "polarity", "X vs Y" | `/triad` |
| "dig deep", "excavate", "what am I not seeing" | `/archaeology` |
| "reframe", "different angle", "spatial" | `/reframe` |
| "wrong conclusion", "reasoning failed" | `/cognitive-debug` |
| "security", "attack", "vulnerability", "threat" | `/threat-model` |
| "ready to ship", "launch", "production ready" | `/launch-gate` |
| "dependency", "vendor", "license", "supply chain" | `/supply-chain-audit` |

## Security Thinking as a Cognitive Mode

The security and production readiness skills (`/threat-model`, `/hardening-audit`, `/launch-gate`, `/incident-ready`, `/supply-chain-audit`) are analytical, but they benefit from cognitive preparation — the same way `/gaps` benefits from running `/archaeology` first.

### Why Security Needs Cognitive Skills

Security analysis tends toward two failure modes:
1. **Checklist compliance** — running through OWASP or CIS benchmarks without reasoning about *this specific system*. Produces findings that are technically correct but not prioritized for the actual risk profile.
2. **Threat theater** — imagining sophisticated attack scenarios while missing the obvious (an unrotated API key, an unvalidated input, a misconfigured CORS header).

The cognitive skills counter both:

| Cognitive skill | What it adds to security analysis |
|----------------|----------------------------------|
| `/archaeology --layers F2,F7` | Surfaces *security assumptions you didn't know you were making* (F2) and *tensions between security and usability* (F7). Example: "We assumed no auth means simpler security" — actually it means a wider anonymous attack surface. |
| `/reframe --searches negative,orthogonal` | **Negative space:** What attack surfaces are conspicuously unaddressed? **Orthogonal:** What if the threat isn't technical but economic (cost runaway) or reputational (content integrity)? |
| `/ghost` | The security-specific hidden dependency detector. What does the security posture implicitly depend on that isn't enforced? (DNS security, vendor 2FA, CI pipeline isolation) |
| `/inversion` | "What if our permissive robots.txt is the attack vector?" "What if the crisis detection system is used to *find* vulnerable seekers rather than help them?" Inverting security assumptions reveals which defenses are load-bearing. |

### Security-Cognitive Compose Recipes

```bash
# Deep threat analysis with cognitive preparation
/compose archaeology --layers F2,F7, threat-model : "the search API"

# Supply chain audit with assumption surfacing
/compose ghost, supply-chain-audit : "our dependency tree"

# Production readiness with full cognitive sweep
/compose archaeology --layers F4,F11, launch-gate : "Phase 0b deployment"

# Security tension mapping
/compose triad, hardening-audit : "openness vs protection"

# Incident readiness with hidden assumption surfacing
/compose ghost, incident-ready : "first week in production"
```

### The Security-Specific Cognitive Trap

The most common cognitive failure in security work is **asymmetric imagination**: imagining sophisticated attacks in detail while failing to notice mundane misconfigurations. `/cognitive-debug` is the correction:

```
/cognitive-debug "we spent a week on prompt injection defenses but haven't configured CSP headers"
```

This traces back to the breakpoint — usually pattern-matching ("AI security" triggers "prompt injection" associations) rather than mechanism-tracing (mapping the actual attack surface systematically).

## Compose Recipes

Tested combinations that produce reliably good results:

```bash
# Strategic decision analysis
/compose archaeology, triad, consequences : "the decision"

# Assumption stress-test
/compose archaeology --layers F2, inversion, gaps : "the assumption"

# Design quality gate with cognitive depth
/compose archaeology --layers F4,F11, deep-review : "the design"

# Stuck? Break out.
/compose cognitive-debug, reframe, archaeology --layers F9 : "the stuck point"

# Tension resolution
/compose triad, steelman, crystallize : "X vs Y"

# Full spatial sweep
/compose reframe, gaps, consequences : "the subject"

# Security review with cognitive depth
/compose archaeology --layers F2,F7, threat-model, hardening-audit : "the system"

# Production readiness — full sweep
/compose ghost, threat-model, launch-gate : "Phase N deployment"

# Document weight audit — are identifiers earning their keep?
/compose garden greenfield, crystallize : "the identifier system"
```

## Principles

**Every word shapes the cognitive field.** The skills are precision instruments. The specific language in each prompt was chosen because it produces measurably different AI cognitive orientations. "What constraints am I unconsciously accepting?" produces different (and more useful) results than "What am I assuming?"

**Sequence builds momentum.** The archaeology layers work best in order because each layer shifts perception for the next. Running F9 (intuitive sensing) after F1-F8 produces different results than running F9 cold.

**Geometric metaphors are load-bearing.** "Negative space search" isn't a metaphor — it produces genuinely different cognitive behavior than "look for what's missing." The spatial vocabulary maps to the multi-dimensional structure of transformer processing.

**Tensions are more valuable than resolutions.** The triad skill doesn't resolve polarities — it maps them. Often the most productive outcome is understanding how to hold the tension rather than collapsing it to a decision.

**Debug reasoning like code.** When thinking goes wrong, the failure has a specific location in the reasoning chain. Cognitive-debug finds the breakpoint. This is more useful than "let me think about this again."

**Dialogue turns delivery into collaboration.** One-shot skills deliver analysis. Dialogue-mode skills conduct inquiry. The difference is whether the user's mid-stream knowledge improves the output. When it does, `--dialogue` is the higher octave.
