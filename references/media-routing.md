# Media Routing and Verification

Use this reference after identifying the communication job. Media classes can
overlap; combine the relevant constraints rather than forcing a single class.
Read [resource-registry.md](resource-registry.md) only when an official
authority or maintained resource is needed for the decision.

## Continuous or variable media

Examples include responsive web documents and browser-based artifacts. Prioritize
semantic structure, reflow, reading order, contrast, and accessible alternatives.
Where the artifact is interactive, also inspect keyboard access, visible focus,
state, and reduced motion as relevant. Essential meaning must not rely on color
alone.

## Finite physical canvas

Examples include printed posters, handouts, reports, and other fixed-size print
artifacts. Start from physical dimensions, observation distance, print area,
export requirements, and printer or venue constraints.

For HTML/CSS print artifacts:

- keep semantic HTML as the editable source;
- define physical dimensions with `@page` and separate screen and print rules;
- use Grid or Flexbox inside the page;
- prefer vector diagrams when practical;
- export a PDF for delivery;
- inspect the rendered PDF and, when possible, critical text, QR codes, and
  raster assets at physical size.

`print-color-adjust: exact` does not guarantee printer output. Printer and venue
requirements govern when they are more specific.

Academic posters are communication situations, not large papers. A viewer
should identify the research question or central claim, principal result, and
why it matters without reading all body text.

## Sequential media

For slides, rebuild density and sequence for spoken presentation. Reuse semantic
roles, figures, and terminology where useful, but do not shrink a poster or
webpage into slides. Check projection readability, the role of each slide, the
spoken sequence, supported structural validation, and rendered slides.

## Motion and video

Treat motion as time-based communication with visual sequence, audio, and
subtitles. Establish how the central message unfolds and how subtitles support
it. Check rendered playback, timing and subtitle readability, and the relation
between sound and visuals. A storyboard alone does not verify playback.

## Short-contact marketing and social media

Prioritize immediate recognition, crop behavior, asset variants, minimum sizes,
clear space, and platform-specific rules. Use brand packages as identity
guidance only within their terms; they are not general-purpose asset libraries.

## Interactive product UI

Choose a design system according to the task: DADS for Japanese public-service
contexts; Material for broad application guidance; Carbon for enterprise and
data-rich interfaces; Fluent for Microsoft-oriented cross-platform interfaces;
Primer for developer-facing products; GOV.UK or USWDS for evidence-driven public
services. Verify semantic structure, focus and keyboard behavior, responsive
behavior, contrast, and state or motion where present.

## Capability boundary

Use an available production or inspection capability only when it is present and
authorized. If a renderer, playback tool, printer access, or medium-specific
skill is unavailable, complete the decisions that can be supported, identify
the missing capability, and give the next verification step. Do not claim a
target-medium check was completed from source inspection alone.
