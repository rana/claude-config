---
name: docs-quality
description: Documentation practice quality review. Use when evaluating whether docs serve AI readers (Claude), human developers, and stakeholders effectively.
argument-hint: "[optional focus area]"
---

Read all project markdown documents to ground in the project's actual state.

## Documentation Quality Review

Evaluate documentation as communication architecture:

1. **AI readability** — Can Claude navigate and understand the docs efficiently? Clear identifiers? Consistent structure? Unambiguous cross-references?
2. **Onboarding** — Could a new developer (human or AI) understand the project from the docs alone? Reading order clear? Dependencies between documents explicit?
3. **Staleness** — Any sections that describe what was rather than what is? Obsolete references? Dead links?
4. **Convention adherence** — Document maintenance rules being followed? Identifier conventions consistent? Section headers follow stated patterns?
5. **Completeness** — Every significant decision documented? Every component described? Every workflow specified?
6. **Redundancy** — Information duplicated across documents? Single source of truth maintained?
7. **Novel approaches** — Are there documentation practices that would improve communication? Anything worth borrowing from other projects or emerging standards?

Focus area: $ARGUMENTS

For every finding:
1. The issue or opportunity
2. The specific location
3. The proposed improvement

Present as an action list. No changes to files — document only.

## Output Management

If the analysis is extensive, deliver the highest-priority findings first. Keep output concise — dense observations, not expansive prose. Note remaining sections available on request.

What questions would I benefit from asking?

What am I not asking?
