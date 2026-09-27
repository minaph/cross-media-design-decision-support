# Anti-patterns for Formative Design and Review

The AP identifiers preserve the source taxonomy. They describe common failure
mechanisms, not universal visual bans. Select relevant entries for an artifact
and medium; a finding needs observable evidence and a communication consequence.
A component can be appropriate when it has a clear role and the target rendering
supports that role.

| ID | Failure mechanism and observable symptom | Counterexample | Formative question | Review evidence | Medium limit |
| --- | --- | --- | --- | --- | --- |
| AP01 | Cardization overload: repeated panels make evidence, examples, and conclusions look equally important. | A comparison table repeats cells to compare the same variable. | Which repeated units genuinely need the same treatment? | Scan path, repeated surfaces, and relative area in the render. | Applies to fixed and fluid layouts; card count alone is not evidence. |
| AP02 | Primary CTA competition: multiple actions look equally primary, so the intended next step is unclear. | One primary action is paired with visibly secondary actions. | What action should this audience take next? | Action labels, relative prominence, and interaction or click path. | Mark not applicable when the artifact has no user action. |
| AP03 | Generic SaaS hero: stock claims, dashboard fragments, and decorative gradients replace a specific communication job. | A landing-page lead names the audience, action, and product evidence. | What makes the lead specific to this artifact and audience? | Lead copy, visual evidence, and relation to the target task. | Primarily applies to product or marketing landing pages. |
| AP04 | Unnecessary dashboard: dense metrics or controls are presented without a decision they support. | A data display answers a named monitoring or comparison task. | Which decision changes when this metric or panel is read? | Metric-to-decision mapping and relevant user task. | Applies to dashboards and data-rich UI; a static chart may instead require AP07. |
| AP05 | Flat hierarchy: primary evidence, caveats, examples, and navigation have similar visual weight. | A reference table deliberately equalizes rows for comparison. | Which evidence must be seen first? | Hierarchy map compared with rendered prominence. | Projection and physical viewing distance change the threshold. |
| AP06 | Abstract copy: headings or claims omit the object, action, evidence, or limit. | A short heading is paired with a concrete subtitle and evidence. | Can a reader name what is acted on and why? | Text plus the nearby source, figure, or action. | Applies across media; short-contact media may require a tighter version. |
| AP07 | Unsupported or fabricated data: a number, proportion, chart, or claim lacks a traceable basis. | A compact caption identifies dataset version, unit, denominator, and aggregation. | Could another reader recompute or correctly bound this value? | Source record, calculation, denominator, unit, version, and limit. | Applies to all media, including static posters and print. |
| AP08 | Cosmetic-only interaction: controls look operable but do not provide the action, state change, or feedback they imply. | A visible control has a working action and discernible state, or a static display avoids control styling. | Does this visual treatment promise an interaction? | Interactive test of action, state, and feedback. | Mark not applicable for noninteractive artifacts. |
| AP09 | Meaningful elements lack semantic identity or accessible names. Symptom: labels, roles, heading structure, or relationships disappear in the source or derivative. | Semantic markup and programmatic names preserve the displayed relationship. | Which visible meanings need a structural or accessible counterpart? | DOM, accessible-name, heading, and source-to-derivative inspection. | Applies to HTML-derived versions; adapt the structural check to the medium. |
| AP10 | Focus and state are absent or ambiguous. Symptom: keyboard focus, selection, error, disabled, or loading states cannot be perceived. | A control keeps a visible focus indicator and distinct states. | Which states can a user enter, and how are they perceived? | Keyboard and state-transition inspection. | Mark not applicable when the artifact has no interactive states. |
| AP11 | Reflow fails. Symptom: content clips, overlaps, requires avoidable two-dimensional scrolling, or loses order at narrow or enlarged views. | A layout preserves reading order and usable controls across supported widths and zoom. | What viewport and zoom constraints must remain usable? | Responsive render at agreed widths and zoom levels. | Applies to variable or responsive media; fixed print needs finite-canvas checks instead. |
| AP12 | Target is unspecified or substituted by a generic audience. Symptom: copy, hierarchy, and action cannot be traced to a viewing context. | An artifact states the intended audience, situation, and purpose. | Who is this for, where do they encounter it, and what should change? | Brief-to-artifact comparison and representative use context. | Applies across media; target evidence differs by artifact type. |
| AP13 | Insufficient contrast: text, boundaries, states, or data encodings cannot be reliably distinguished. | Contrast and redundant cues support the intended reading task. | Which distinctions remain legible under target conditions? | Contrast measurement where applicable and target-render inspection. | Print, projection, and web need medium-specific conditions. |
| AP14 | Form labels or error recovery are missing. Symptom: a field relies on placeholder text, or error messages do not identify and explain recovery. | Persistent labels and associated, actionable error messages. | Can a user identify each field and recover from an invalid entry? | Form, keyboard, and error-state inspection. | Mark not applicable when the artifact has no form input. |
| AP15 | Tokens and states are inconsistent. Symptom: the same semantic role changes appearance without reason, or distinct states look the same. | Role-oriented tokens and documented component states maintain intended distinctions. | Which roles and states must remain consistent across screens or derivatives? | Token use, component comparison, and state inventory. | Most relevant to systems and UI; use proportionately for static artifacts. |
| AP16 | Excessive motion distracts, obscures state change, or ignores user motion preferences. | Motion establishes sequence or feedback and can be reduced. | What information does this motion convey, and can it be reduced safely? | Playback, timing, and reduced-motion inspection. | Mark not applicable when the artifact has no motion. |

## Cross-media supplementary questions

These questions arose from cross-media formation and review. They are separate
from the AP identifiers above so source tracking remains intact.

- **Space allocation:** compare adding evidence, improving an existing
  explanation, visualizing dense material, and retaining space. Choose additions
  by value, evidence, and reading burden.
- **Research limits:** make copy concrete by restoring its object, action, and
  evidence while retaining uncertainty, retrospective status, scope, and causal
  limits that change the warranted conclusion.
- **Unwarranted scores:** do not make source coverage, item counts, or
  "AI-like" appearance into quality thresholds without a valid basis.
- **Derivative-media adaptation:** preserve semantic roles and source/analysis
  distinctions while adapting layout and sequence for the target medium.
- **Implementation and communication:** report build or export success
  separately from evidence that the artifact communicates effectively.
- **Resource routing:** use a design system, asset library, or authority only
  when it governs a stated decision and fits its terms and scope.

## Using the table

For formation, select the relevant APs once before committing the first
structure. For a revision review, select the APs relevant to the changed
artifact before making findings. Do not require every AP when the artifact or
medium lacks the associated feature; record it as not applicable rather than
manufacturing a finding.
