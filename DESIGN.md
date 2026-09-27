# Design Notes

This document records the design rationale behind `cross-media-design-decision-support`. It is intentionally separate from `SKILL.md`: the skill file contains runtime instructions, while this file preserves the research-derived architecture, resource registry, maintenance policy, and boundaries that explain those instructions.

The source is the user-supplied ChatGPT Deep Research report titled "媒体横断・ウェブ親和型デザイン資源の比較研究と、学会ポスター制作を含むエージェントスキル設計", dated 2026-09-27. Its JSON export is retained locally at `tmp/report.json` and is not distributed. The export includes conversation metadata and session-local citation identifiers; its claims are research inputs, not independently reverified facts. The registry below provides public source routes, but is not a complete claim-to-source audit of that report.

The report's motion coverage concerns time-based communication, audio/subtitles, timeline checks, and cross-media brand operations. The skill adopts that limited scope; it does not infer a general video-production method or add encoding requirements from the report.

## 1. Clarifying the two directory trees in the research report

The research report contains two closely related directory trees:

```text
design-package/
├── SKILL.md
├── principles/
├── media/
├── tokens/
├── assets/
├── templates/
├── references/
└── validation/
```

and, later inside the proposed skill instructions:

```text
package/
├── SKILL.md
├── principles/
├── media/
├── tokens/
├── assets/
├── templates/
├── references/
└── validation/
```

They describe the same conceptual pattern at two different levels of the report.

- The first is introduced as a **template for organizing a reusable design system or design package** that the skill may help a user create.
- The second embeds that recommendation into the proposed skill itself as an instruction for future package-generation tasks.

They are therefore **not the required repository tree of this Agent Skill**.

The current skill can remain much smaller because it does not bundle fonts, icons, templates, scripts, or design-token files. It primarily bundles procedural knowledge and a curated routing registry.

## 2. Core architecture: A / B / C

The research converged on three layers.

### A. General judgment

This is not a separate module; it is the stance applied throughout the workflow.

The agent should clarify:

- audience;
- task or communication job;
- context of use;
- central message;
- information hierarchy;
- readability;
- accessibility;
- visual emphasis;
- validation needs.

The purpose is to prevent local styling conventions from substituting for communication logic.

### B. Medium routing

The same concept of “readability” has different implementation consequences in different media.

The skill therefore distinguishes, before implementation:

- continuous or variable media;
- finite fixed canvases;
- sequential media;
- interactive media;
- short-contact marketing/social media.

This routing determines which technical or domain authority should be consulted.

### C. Resource routing

The skill should maintain known first-choice resources rather than repeat an unrestricted search for every task.

The agent should search beyond the registry when a known resource does not fit or when current facts such as version, URL, license, or usage terms need confirmation.

## 3. Why the skill does not copy one design system

The compared systems are authoritative in different scopes.

Examples:

- W3C specifications govern CSS behavior.
- WCAG governs web accessibility criteria.
- GOV.UK, USWDS, and DADS are especially strong for evidence-driven service design, structure, accessibility, and implementation examples.
- Material, Carbon, Fluent, and Primer are strong component/token ecosystems for product UI.
- Apple and public-sector brand kits are useful examples of cross-media asset governance, but their proprietary visual assets are not generic building blocks.
- Academic-poster guidance addresses communication goals rather than CSS implementation.

The design rule is therefore:

> identify the problem type first, then consult the authority that owns that problem.

## 4. Resource registry

This registry records first routes, not universal winners. Re-check current URLs, versions, licenses, and usage conditions when they materially affect a deliverable.

### General web and public-service structure

**DADS — Digital Agency Design System**  
https://design.digital.go.jp/dads/

Use for Japanese-language web/service-design guidance, accessibility, Figma, code, tokens, documentation, and related assets.

**GOV.UK Design System**  
https://design-system.service.gov.uk/

Use for evidence-driven public-service content, layout, accessibility, and implementation examples.

**U.S. Web Design System (USWDS)**  
https://designsystem.digital.gov/

Use for public-service web patterns, tokens, code, and design kits.

### Product UI and tokens

**Material 3**  
https://m3.material.io/

Use for broad application UI, component, token, and interaction guidance.

**IBM Carbon**  
https://carbondesignsystem.com/

Use for enterprise and data-rich product interfaces.

**Microsoft Fluent 2**  
https://fluent2.microsoft.design/

Use for Microsoft-oriented and cross-platform product UI.

**GitHub Primer**  
https://primer.style/

Use for developer-oriented product UI, primitives, accessibility, and Octicons integration.

### General-purpose icons

**Material Symbols**  
https://developers.google.com/fonts/docs/material_symbols

Broad semantic icon vocabulary; commonly available as SVG/PNG and font forms. Confirm current license and distribution terms at use time.

**Fluent System Icons**  
https://github.com/microsoft/fluentui-system-icons

Large coherent interface icon family with SVG and platform packages. Confirm current repository license at use time.

**Primer Octicons**  
https://primer.style/octicons/

SVG-first icon set particularly suitable for developer and tooling concepts. Confirm current license at use time.

### Japanese explanatory illustrations

**Digital Agency illustrations and icons**  
https://www.digital.go.jp/policies/servicedesign/designsystem/Illustration_Icons

Use when the visual language and usage conditions fit Japanese administrative or explanatory communication. Check current print/color notes and terms before reuse.

### Print and HTML-to-print

**W3C CSS Paged Media**  
https://www.w3.org/TR/css-page-3/

Use for page dimensions, orientation, and paged-media behavior in CSS.

**W3C CSS Color Adjustment**  
https://www.w3.org/TR/css-color-adjust-1/

Use for the semantics and limits of print color adjustment.

### Accessibility

**WCAG 2.2**  
https://www.w3.org/TR/WCAG22/

Use as the web-accessibility baseline where applicable.

### Academic posters

**PLOS — Ten Simple Rules for a Good Poster Presentation**  
https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.0030102

Use for poster communication goals, rapid recognition, title/claim framing, and content prioritization. Do not use it as a CSS or print-production specification.

### Cross-media identity and brand operations

**Apple App Store Marketing Resources**  
https://developer.apple.com/app-store/marketing/guidelines/

Use as a reference for coordinating digital and print asset rules. Proprietary brand assets remain governed by Apple’s current terms.

**Digital Agency logotype kit**  
https://www.digital.go.jp/applications/logotype

Use as an example of parallel screen/print sizing and asset variants. Follow current usage conditions for the actual marks.

**Digital Marketplace Visual Identity**  
https://www.digital.go.jp/policies/dmp

Use as an example of cross-media visual-identity governance.

## 5. Academic-poster implementation decision

For an academic poster built with HTML/CSS, the research supports the following separation of responsibilities:

- semantic HTML is the editable source of truth;
- CSS tokens carry reusable visual roles;
- physical page dimensions are explicit;
- screen CSS provides preview behavior;
- print CSS provides finite-canvas behavior;
- PDF is a derived delivery/print artifact;
- final validation targets the rendered PDF and, where possible, physical-size checks.

This structure permits the same content, figures, and tokens to be adapted to web pages, slides, and social assets without pretending those media share the same layout.

## 6. Why `README.md`, `SKILL.md`, and `DESIGN.md`

### `README.md`

Audience: humans evaluating or installing the repository.

Keep:

- project purpose;
- research summary;
- scope and non-goals;
- repository structure;
- installation/use overview;
- maintenance date;
- license notice.

Do not place detailed runtime procedures here.

### `SKILL.md`

Audience: compatible agents after skill activation.

Keep:

- frontmatter and trigger description;
- operational workflow;
- medium classification;
- routing protocol;
- validation rules;
- output contract;
- direct references to `DESIGN.md` when detailed registry or rationale is needed.

Keep it concise because agents load the full file after activation.

### `DESIGN.md`

Audience: maintainers and agents that need detailed routing context.

Keep:

- architecture rationale;
- the A/B/C distinction;
- explanation of the report’s package trees;
- detailed resource registry;
- provenance and maintenance policy;
- design tradeoffs;
- boundaries and rejected interpretations.

This file may later be split into `references/` if it grows substantially or different parts need independent loading.

## 7. When to expand the repository

Do not create directories merely because the research report showed them.

Expand only when the repository actually contains the corresponding responsibility:

- `references/` when detailed runtime references become large or independently loadable;
- `assets/` when templates, images, lookup data, or bundled examples are added;
- `scripts/` when executable validation or conversion logic is added;
- `templates/` when the skill begins shipping concrete starter artifacts;
- `validation/` when checklists become large enough to deserve independent maintenance.

If a resource is only an external URL in the registry, it does not require a local `assets/` directory.

## 8. Maintenance policy

The research snapshot is dated **2026-09-27**.

Stable claims should be separated from time-sensitive claims.

Relatively stable:

- purpose-before-style workflow;
- medium classification;
- separation of authority by problem type;
- rendered-artifact validation;
- distinction between guides and reusable assets.

Time-sensitive:

- URLs;
- versions;
- file formats;
- license terms;
- proprietary-brand usage rules;
- exact contents of design kits.

When maintaining the skill, update time-sensitive facts without rewriting the stable architecture unless new evidence changes the routing model itself.
