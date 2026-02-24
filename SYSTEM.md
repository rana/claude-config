# System

What this is, how it's structured, and how to maintain it.

## Identity

A personal cognitive toolkit for Claude Code. 28 skills in 6 families, 4 documents, and a set of commands — designed to shape how Claude sessions analyze, decide, and build.

The audience is AI. These files are read by Claude at session start. They work by shaping cognitive orientation — the specific language in skill prompts produces measurably different analytical behavior. This isn't configuration. It's cognitive infrastructure.

## Architecture

Four documents, each at a different altitude:

| Document | Altitude | Question it answers |
|----------|----------|-------------------|
| SYSTEM.md (this) | Identity | What is this system? |
| SKILLS.md | Reference | What skills exist and when do I use them? |
| SKILL-SYSTEM.md | Doctrine | How do I wield the full system effectively? |
| COGNITIVE-GUIDE.md | Depth | How do the 4 cognitive steering skills work? |

**Reading order:** SYSTEM.md → SKILLS.md → SKILL-SYSTEM.md → COGNITIVE-GUIDE.md. Each assumes familiarity with what precedes it, though any can be read standalone.

**Design principle:** No document duplicates another. SKILLS.md is the catalog. SKILL-SYSTEM.md is the operational playbook across all 28 skills. COGNITIVE-GUIDE.md goes deep on 4. This document holds the architecture they all live inside.

## Skill Anatomy

Every skill definition (`skills/<name>/SKILL.md`) follows a consistent structure:

```
---
name: <skill-name>
description: <one-line>
argument-hint: "<usage pattern>"
---

Read all project markdown documents to ground in the project's actual state.

## <Analysis Protocol>

[The skill's specific methodology]

## Output Management

**Hard constraints:**
- Segment output into groups of up to N findings
- Write each segment incrementally
- After each segment, continue immediately to the next
- Continue until ALL findings are reported

[Closing questions]
```

**Conventions that matter:**
- **Read all project markdown documents** — skills ground in the target project's docs, not this system's docs (unless this system is the target)
- **Hard constraints** — prevent unbounded responses; segment sizes cap each output chunk, not the total work
- **Automatic continuation** — after each segment, continue immediately without waiting for user input. The segment size prevents token-limit timeouts; automatic continuation ensures completeness
- **Write incrementally** — deliver findings as they emerge, don't accumulate
- **Closing questions** ("What questions would I benefit from asking?") — seed meta-cognition; they're functional, not decorative
- **"You have complete design autonomy"** — appears in cognitive skills to unlock creative capacity; it's a precision instrument
- **Skills are read-only** — they propose changes but never modify files
- **Every finding** includes: what, where, proposed action

## Directory Structure

```
~/.claude/
├── SYSTEM.md                # Identity and architecture (this file)
├── SKILLS.md                # Skill reference catalog
├── COGNITIVE-GUIDE.md       # Cognitive skill playbook
├── SKILL-SYSTEM.md          # Operational doctrine
├── settings.json            # Claude Code configuration
│
├── skills/                  # Skill definitions (28 native + 1 external)
│   ├── archaeology/SKILL.md
│   ├── crystallize/SKILL.md
│   ├── ...
│   └── neon-postgres → ../../.agents/skills/neon-postgres
│
├── plugins/                 # Installed Claude Code plugins (project-scoped)
├── plans/                   # Ephemeral — work plans from any project
├── todos/                   # Ephemeral — session task tracking
└── cache/                   # Ephemeral — changelog, stats
```

**Dual nature.** This directory is both the toolkit (skills, documents — durable, version-controlled) and cross-project working memory (plans, todos, cache — ephemeral, gitignored). They coexist because Claude Code scopes `~/.claude/` globally. The durable layer is the system. The ephemeral layer is the system in use.

**External skills.** `neon-postgres` is a symlink to a skill definition outside this repo. All other skills are native. If more external skills appear, establish a convention for distinguishing them.

## Ecosystem

This toolkit is global — available to every Claude Code session regardless of project. Individual projects have their own CLAUDE.md files that may reference these skills, and project-scoped plugins that add capabilities beyond this system.

**Elmer** (autonomous exploration engine) is a separate system that can invoke these skills in background sessions. The two systems complement each other — interactive cognitive toolkit + autonomous exploration engine — but they haven't been unified. See COGNITIVE-GUIDE.md §Integration with Elmer for the current relationship.

## Self-Maintenance

The toolkit is subject to the same entropy it's designed to detect in other projects. Documents drift. Skills accumulate rather than compose. Conventions erode.

**The self-maintenance loop:**

```bash
# Are the skills earning their keep?
/compose garden greenfield, crystallize

# Are the documents telling a consistent story?
/coherence

# Has the system drifted from its stated architecture?
/drift-detect

# What's implicit that should be explicit?
/ghost
```

**When to run:** After adding skills. After significant restructuring. When the system feels heavier than it should. When something feels off but you can't articulate it.

**The principle:** A toolkit that can't maintain itself can't credibly maintain anything else.

## Origin

This system was built through accretion, then composed. The git history tells the story:

1. Initial config backup
2. 9 analytical skills + 4 commands
3. Output management hardening across all skills
4. 4 cognitive steering skills + calibrate + cognitive guide
5. 5 security and production readiness skills
6. Garden skill for identifier lifecycle
7. Greenfield reconstructibility lens added to garden, crystallize, docs-quality
8. Operational doctrine (SKILL-SYSTEM.md) for the full 28-skill system
9. This document — the system's self-portrait

Each layer was a response to something missing. The system grew until it needed to know what it was.
