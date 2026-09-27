---
name: cross-media-design-decision-support
description: >
  Structures ambiguous design requests by audience, purpose, information hierarchy,
  medium, implementation constraints, and validation needs; then routes work to
  appropriate official guidance and known design resources. Use for web, print,
  academic posters, slides, marketing/social assets, motion, product UI, or
  cross-media design work, including HTML/CSS-based print artifacts.
---

# Cross-media Design Decision Support

## Mission

Turn design requests into explicit, medium-appropriate decisions before styling.

Do not choose a vendor design system as an aesthetic shortcut. First identify the communication job and the type of medium, then use the authority or asset library that actually governs that problem.

For detailed rationale, resource provenance, and the maintained resource registry, read [DESIGN.md](DESIGN.md) when relevant.

## 1. Establish the design job

Before choosing colors, fonts, grids, cards, icons, or components, determine as much of the following as the request supports:

- primary audience;
- viewing or use context;
- primary job of the artifact;
- central message or action;
- primary medium;
- derivative media;
- physical or viewport constraints;
- interaction requirements;
- brand or institutional constraints;
- accessibility requirements;
- content density and data requirements;
- submission, export, or delivery requirements.

Do not ask again for facts the user already supplied. If missing information does not block useful progress, state a reasonable assumption and continue.

## 2. Build information structure before visual style

Create the smallest useful hierarchy:

1. express the central message in one sentence;
2. identify the first thing the audience should notice;
3. separate primary, supporting, and reference information;
4. determine reading order, interaction order, or presentation sequence;
5. only then choose typography, color, layout, boundaries, icons, and component patterns.

Use strong visual distinctions only when they carry an information role.

If a local styling problem persists, move one level upward and check whether the real problem is hierarchy, grouping, sequence, terminology, or content density.

## 3. Establish a compact token system

When implementation is required, define a small portable token set before detailed styling.

Prefer role-oriented names such as:

```css
:root {
  --color-ink: ...;
  --color-muted: ...;
  --color-accent: ...;
  --color-surface: ...;

  --space-1: ...;
  --space-2: ...;
  --space-3: ...;
  --space-4: ...;

  --type-display: ...;
  --type-heading: ...;
  --type-body: ...;
  --type-caption: ...;
}
```

Across derivative media, preserve semantic roles and hierarchy where possible, while allowing layout, density, and sequencing to change.

## 4. Classify the medium

Use the following design classes before routing to resources.

### Continuous or variable media

Examples: responsive web documents and many browser-based artifacts.

Prioritize:

- semantic structure;
- reflow and responsive behavior;
- reading order;
- keyboard and focus behavior when interactive;
- contrast and accessibility;
- progressive enhancement;
- rendered QA.

Useful first routes include DADS, GOV.UK Design System, USWDS, Material 3, Primer, Carbon, and Fluent 2. Use WCAG for accessibility requirements.

### Finite physical canvas

Examples: printed posters, handouts, and other fixed-size print artifacts.

Start from physical dimensions, observation distance, print area, export requirements, and printer or venue constraints.

For HTML/CSS print artifacts:

- keep semantic HTML as the editable source;
- define the physical page in physical units;
- use `@page` and separate screen/print rules;
- use Grid/Flexbox inside the page;
- prefer vector diagrams where practical;
- export a PDF for delivery;
- inspect the rendered PDF, not only the source.

Use W3C CSS Paged Media and CSS Color Adjustment for implementation behavior. Follow venue and printer specifications when they are more specific.

### Sequential media

Examples: presentation slides.

Rebuild information density and sequence for spoken presentation. Reuse tokens, figures, visual motifs, and terminology where useful, but do not shrink a poster or webpage into a slide deck.

Validate both file structure and rendered slides.

### Short-contact marketing or social media

Prioritize immediate recognition, crop behavior, asset variants, minimum sizes, clear space, and medium-specific rules.

Brand-resource packages are references for operating a visual identity across media. They are not general-purpose asset libraries unless their terms explicitly permit that use.

### Interactive product UI

Choose a system according to the problem:

- DADS for Japanese public-service and accessibility-oriented contexts;
- Material 3 for broad component and UI guidance;
- Carbon for enterprise and data-rich systems;
- Fluent for Microsoft-oriented and cross-platform UI;
- Primer for developer-oriented product interfaces;
- GOV.UK or USWDS for evidence-driven public services.

## 5. Special case: academic posters

Treat the poster as a communication situation, not a large paper.

A viewer should be able to identify, without reading all body text:

- the research question or central claim;
- the principal result;
- why the result matters.

If the poster is authored in HTML/CSS, the print canvas is the primary physical constraint while the HTML remains an editable semantic source.

A conservative page shell is:

```css
:root {
  --page-w: 1189mm;
  --page-h: 841mm;
}

.poster {
  width: var(--page-w);
  min-height: var(--page-h);
}

@page {
  size: 1189mm 841mm;
  margin: 0;
}

@media print {
  .poster {
    transform: none;
  }
}
```

Do not assume `print-color-adjust: exact` guarantees final printer output. Inspect the exported PDF and follow the actual printer or conference specification.

## 6. Resource selection protocol

Do not begin with open-ended searches for icons, design systems, or generic assets.

Use the maintained registry in [DESIGN.md](DESIGN.md) first. Prefer official sources and record:

- official name;
- official URL;
- what the resource contains;
- the problem it addresses;
- limitations or contexts where it does not apply;
- license or usage conditions when relevant.

Browse or research further when:

- a known resource does not satisfy the requirement;
- current version, URL, license, or usage conditions may have changed;
- a project-specific standard, brand guide, printer requirement, or institutional rule overrides the generic registry.

## 7. Validate the artifact, not only the source

### Universal

Check:

- the central message is still visible;
- reading or interaction order is clear;
- every strong visual element has a job;
- typography and spacing are systematic;
- the design has not drifted into an unrelated vendor identity;
- the actual target-medium rendering was inspected.

### Web

Check:

- semantic structure;
- visible focus and keyboard behavior where relevant;
- contrast;
- responsive or reflow behavior;
- reduced motion where relevant;
- no essential meaning encoded only by color.

### Print and posters

Check:

- correct physical page size;
- no overflow or clipping;
- adequate raster resolution;
- vector graphics retained where appropriate;
- critical backgrounds and colors survive export;
- QR codes and small labels at physical size;
- venue or printer bleed and color requirements;
- final PDF visually inspected.

### Slides

Check:

- readability under projection;
- each slide has a clear role;
- sequence supports the spoken narrative;
- structural validation where supported;
- rendered slides visually inspected.

## 8. Self-critique

Perform one deliberate second pass.

Ask:

1. What is the single most important element?
2. What competes with it without a clear reason?
3. Which visual distinction can be removed?
4. Which styling problem is actually an information-architecture problem?
5. Has a vendor design system become the aesthetic instead of a resource?
6. Are selected assets and usage conditions explicit?
7. Was the actual target-medium rendering inspected?

Prefer hierarchy correction, refinement, and removal over decorative additions.

## 9. Output contract

For substantial design planning, provide:

1. context and primary design job;
2. audience and medium classification;
3. information hierarchy;
4. compact token or design direction;
5. medium-specific decisions;
6. named official resources and why they apply;
7. applicability limits;
8. implementation plan;
9. validation plan;
10. remaining uncertainty or external constraints.

Do not return an unconnected list of design links. Tie every resource to a concrete design decision.
