# Cognitive Toolkit

This directory (`~/.claude/`) is a personal cognitive toolkit for Claude Code — 33 skills and 9 commands that shape how sessions analyze, decide, and build. It is both the toolkit (skills, commands, documents — durable, version-controlled) and cross-project working memory (plans, todos, cache — ephemeral, gitignored).

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
[Methodology]

## Output Management
**Hard constraints:**
- Segment output into groups of up to N findings
- Write each segment incrementally
- After each segment, continue immediately to the next
- Continue until ALL findings are reported

[Closing questions]
```

**Conventions that matter:**
- "Read all project markdown documents" grounds in the **target project's** docs, not this toolkit's docs
- Output management segments prevent token-limit timeouts; auto-continuation ensures completeness
- Skills are read-only — they propose changes but never modify files
- Closing questions ("What am I not asking?") seed meta-cognition — functional, not decorative
- "You have complete design autonomy" in cognitive skills unlocks creative capacity — it's a precision instrument
- Skill prompts are precision instruments — specific wording produces measurably different cognitive behavior. Do not paraphrase when editing

## Validation

When editing or adding skills, verify:
- Frontmatter has `name`, `description`, `argument-hint`
- Output management section exists with segment size and auto-continue instruction
- No references to skills that don't exist (check `ls skills/`)
- Skill count in SYSTEM.md matches actual count (currently 33: 32 native + 1 external symlink)
- Cross-references between skills are accurate

## Self-Maintenance

```bash
/doc-health           # identifier audit + consistency
/drift-detect         # stated vs actual architecture
/ghost                # hidden assumptions
/crystallize          # simplification opportunities
```

Run after adding skills, after restructuring, or when the system feels heavier than it should.

## Structure

```
~/.claude/
├── CLAUDE.md              # AI context (this file, auto-loaded in .claude/ sessions)
├── SYSTEM.md              # Human reference (recipes, selection, cognitive guide)
├── settings.json          # Claude Code configuration
├── skills/                # 33 skill definitions
├── commands/              # 9 command definitions
├── plugins/               # Installed Claude Code plugins
├── plans/                 # Ephemeral — work plans from any project
├── todos/                 # Ephemeral — session task tracking
└── cache/                 # Ephemeral — changelog, stats
```
