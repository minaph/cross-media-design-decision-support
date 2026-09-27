# Cross-media Design Decision Support

A portable Agent Skill for structuring ambiguous design requests, routing them to medium-appropriate guidance, and validating the rendered result.

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
├── README.md   # Human-facing overview, research summary, usage and maintenance notes
├── SKILL.md    # Agent-facing operational instructions
└── DESIGN.md   # Design rationale, A/B/C architecture, resource registry and maintenance decisions
```

No license has been selected yet. MIT is under consideration; a `LICENSE` file and matching optional `license` field in `SKILL.md` will be added when adopted.

The larger `principles/`, `media/`, `tokens/`, `assets/`, `templates/`, `references/`, and `validation/` tree described in the research report is **not the required repository structure of this skill**. It is a downstream packaging template the skill may recommend when organizing a reusable design system or cross-media design package.

## Skill name

The skill name is:

```text
cross-media-design-decision-support
```

When the repository root itself is the skill directory, keeping the repository name identical to the `name` field avoids ambiguity and follows the Agent Skills naming convention.

## Use

Install or expose this repository as a skill directory in a client that supports the Agent Skills format. The client should discover the YAML frontmatter in `SKILL.md`, load the instructions when the description matches a design task, and read `DESIGN.md` when detailed routing, resource selection, provenance, or maintenance rationale is needed.

## Maintenance

The research snapshot was prepared on **2026-09-27**. The skill should treat URLs, package versions, licenses, and proprietary-brand usage terms as time-sensitive. Re-check those facts when they materially affect a deliverable.

The stable part of the skill is the routing logic: define the communication job, classify the medium, select the authority appropriate to that problem, and validate the actual rendered artifact.
