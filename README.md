# Cross-media Design Decision Support

A portable Agent Skill for developing design decisions, routing work to medium-appropriate guidance, and reviewing the rendered result.

The skill separates **formative support** (choosing content, hierarchy, and layout while developing an artifact) from **review support** (assessing a specific version with evidence). A compact entry point routes to references for each mode. The modes share the same communication purpose and can alternate as new feedback arrives.

The skill owns design decisions and acceptance criteria. It hands production to available medium-specific skills or tools when requested; it does not bundle a rendering or video-editing toolchain. Planning-only work ends with the requested design brief.

This repository turns a comparative review of design systems, design resources, and agent design skills into an operational skill. The central idea is not to copy a particular vendor aesthetic. Instead, the skill separates three responsibilities:

1. **General design judgment** — clarify audience, purpose, context, information hierarchy, readability, accessibility, and the role of strong visual distinctions.
2. **Medium routing** — distinguish continuous/responsive media, finite physical canvases, sequential media, and interactive media before choosing implementation guidance.
3. **Resource routing** — prefer a small registry of known official resources over open-ended asset search, then verify current versions, URLs, licenses, and usage conditions when needed.

The research basis included Anthropic design-related Skills, Apple design and marketing resources, Google Material resources, Japan Digital Agency DADS, IBM Carbon, Microsoft Fluent, GOV.UK Design System, U.S. Web Design System, GitHub Primer, W3C specifications, WCAG, and academic-poster guidance.

## Why this skill exists

Design requests often combine several different problems: communication goals, information architecture, layout, visual style, implementation constraints, accessibility, print constraints, and asset selection. Treating all of them as “choose a good-looking design system” obscures which authority should govern which decision.

This skill therefore asks the agent to identify the problem class first and select the relevant guidance second. For example:

- W3C specifications govern CSS and paged-media behavior, but not how a research result should be framed.
- Academic-poster guidance helps define communication goals, but not CSS print behavior.
- UI design systems provide components and tokens, but their visual identity should not automatically become the aesthetic of a poster or report.
- Icon libraries are reusable assets, not general design methodologies.

## Repository structure

```text
cross-media-design-decision-support/
├── README.md
├── SKILL.md                         # Mode selection, common constraints, output contract
├── DESIGN.md                        # Alternatives, rationale, provenance, maintenance
├── references/
│   ├── formative-design.md          # Content and structure decisions
│   ├── artifact-review.md           # Evidence-based findings and rechecks
│   ├── anti-patterns.md              # Failure mechanisms, exceptions, medium limits
│   ├── media-routing.md             # Medium-specific production and validation
│   └── resource-registry.md         # Known official resources
└── docs/
    ├── poster-design-recap.md        # Case history and lessons from delegated work
    └── validation.md                # Checks performed and their limits
```

No license has been selected yet. MIT is under consideration; a `LICENSE` file and matching optional `license` field in `SKILL.md` will be added when adopted.

The larger package tree in the original research report is a downstream design-package example, not a requirement to create empty directories. The references here each have a concrete, independently loadable responsibility.

## Skill name

The skill name is:

```text
cross-media-design-decision-support
```

When the repository root itself is the skill directory, keeping the repository name identical to the `name` field avoids ambiguity and follows the Agent Skills naming convention.

## Use

Install or expose this repository as a skill directory in a client that supports the Agent Skills format. The client discovers the YAML frontmatter in `SKILL.md`, selects formative support, review support, or both, and follows the relevant reference links. Read `DESIGN.md` for architecture and provenance rather than loading every reference for every task.

Example requests:

- "There is unused space in this poster. Compare useful additions and revise the overall layout."
- "Review this slide deck for competing messages and generic repeated panels; preserve justified comparisons."
- "This interface feels generic. Diagnose the information relationships and verify the actual interactions."
- "Adapt this poster to a narrated sequence, keeping the evidence and uncertainty clear."

Anti-patterns are prompts for contextual judgment. Cards, gradients, repeated structures, or empty space are not automatically defects. Web-specific checks do not stand in for print or time-based validation. The skill does not assign a universal AI-design score.

The [case recap](docs/poster-design-recap.md) explains the source material and observed revisions. The [design decisions](DESIGN.md) compare putting the report directly into `SKILL.md`, keeping a separate report, using multiple references, and splitting into separate skills. The selected architecture uses one entry point with separate formative and review references.

## Maintenance

The original research snapshot was prepared on **2026-09-27**; the case-informed restructuring is dated **2026-09-28**. The skill should treat URLs, package versions, licenses, and proprietary-brand usage terms as time-sensitive. Re-check those facts when they materially affect a deliverable.

The stable part of the skill is the routing logic: define the communication job, classify the medium, select the authority appropriate to that problem, and validate the actual rendered artifact.
