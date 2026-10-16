---
name: figma-to-frontend-page
description: Implement or update a frontend page, section, or component from a Figma URL in the current repository, including asset reuse and browser verification. Use for Figma-to-code implementation requests, not design-only analysis or writing designs into Figma.
---

# Figma to Frontend Page

## Outcome and scope

Implement the selected design in the existing project and verify the result in a browser. A Figma URL is normally sufficient to begin; infer project conventions from the repository. Accept supplied screenshots or exports as fallback evidence when the design cannot be accessed.

User instructions take precedence over these guidelines. Preserve existing changes and keep edits within the requested scope. Identify whether the task is a new page, an existing-page update, a section, or a reusable component before choosing files or routes. Do not turn a component or local correction into a new page.

## Core constraints

- Read the relevant repository code before editing. Reuse its framework, router, styling, tokens, components, assets, and data conventions when suitable.
- Translate design geometry into layout rules. Prefer normal flow, flex, and grid; use absolute positioning for actual overlap, decoration, or overlays. Figma groups are evidence, not mandatory component boundaries.
- Reuse identical assets and suitable mapped components. Preserve distinctive imagery and icons rather than substituting approximate symbols. Do not render an entire interactive section as a screenshot.
- Implement behavior supported by requirements, prototypes, or existing product behavior. Do not infer sticky positioning, filter semantics, API contracts, or navigation destinations from appearance alone.
- Preserve semantic controls, accessible names, keyboard operation, and appropriate focus behavior. Exclude device chrome such as an OS status bar unless requested.
- Do not claim visual parity without comparing the implemented target against the design. Report blocked or unverified requirements explicitly.

## CSS compatibility

- Use `margin` for spacing between flex, grid, and repeated items. Do not use `gap`, `row-gap`, or `column-gap`. Put spacing on a named item class; give the first or last item an explicit modifier class when its margin differs. Do not replace `gap` with selectors such as `> * + *`, `:first-child`, or `:last-child`.
- Write selectors against explicit component classes. Avoid universal selectors and sibling combinators (`+`, `~`) in styles that may compile to WXSS. Check the target platform's selector support before using other pseudo-classes or combinators; do not assume browser CSS support implies WXSS support.
- For masks and fixed panels, use explicit `top`, `right`, `bottom`, and `left` declarations instead of `inset`. When using `env(safe-area-inset-*)`, put a plain-value fallback immediately before the declaration that uses `env()`. Set `box-sizing: border-box` where fixed widths and padding must fit together.
- In Taro H5, the built-in `taro-button-core:active` style can turn a pressed button gray even when its hover class is disabled. If the design has no pressed-color change, override the active background and text colors for the specific button classes, preserving each button's normal colors. Do not reset buttons globally or change disabled styling.

## Evidence and decisions

Read [design-evidence.md](references/design-evidence.md) when gathering or refreshing design evidence. Keep a concise working summary of the target, project conventions, asset mapping, applicable capabilities, and uncertainties. Context notes are sufficient for small tasks; do not generate a specification file unless useful or requested.

Classify decisions:

- **Confirmed:** explicit user requirements, selected design properties, prototype behavior, or relevant existing product contracts.
- **Inferred:** ordinary layout adaptation, wrapping, and local component boundaries consistent with the project. Choose the smallest reasonable implementation and disclose material assumptions.
- **Unknown:** missing submission contracts, ambiguous destinations, conflicting target frames, or consequential business behavior. Inspect available evidence first; ask a focused question if still required. Continue independent work while awaiting an answer.

A visible control alone does not establish its business behavior. Do not fake successful submissions, invent endpoints, or silently substitute mock behavior. Use fixtures only when the task or existing preview convention supports them and identify that limitation.

## Execution

Follow dependencies rather than repeating a fixed sequence. For a local correction, reuse still-valid evidence and inspect the changed region plus affected shared behavior. Independent repository and design reads may be batched.

### 1. Identify target and project

Parse the file key and node ID. Inspect the selected node's type, dimensions, and surrounding context. If the node ID is absent, inspect top-level candidates; select only when the target is clear.

Use targeted searches and reads to establish:

- applicable repository instructions and current changes;
- package manager, development and verification commands;
- likely destination files and the closest existing implementation;
- router, styling, tokens, fonts, viewport/unit handling, and component conventions;
- existing design-to-code mappings and assets where available.

For existing-page or component work, preserve its entry point. For a new page, follow the existing route family and parameter conventions, checking conflicts. Use the frame name only as a fallback naming hint; do not impose a generic detail route.

### 2. Acquire sufficient design evidence

Prefer available Figma tools for metadata, screenshots, variables, component mappings, and assets. Follow any required tool-specific skill prerequisites before calling those tools. If access fails, try an available authenticated browser, then supplied screenshots or exports. Do not use web search as a substitute for the actual design.

Start with the target screenshot and structural overview, then fetch details for relevant subtrees. Inspect below-the-fold content. Do not repeatedly retrieve the entire file or unrelated frames. Record unavailable measurements or states as uncertainty rather than exact facts.

### 3. Map and implement

Map the design into meaningful modules, choosing existing components where their behavior and appearance fit. Extract a component when reuse, independent behavior, or complexity justifies it; do not split every wrapper or create a design system for one page.

Resolve fonts and major assets early. Preserve asset aspect ratio, transparency, and appropriate resolution; use repository storage conventions and semantic filenames. Check that runtime assets load from a durable location supported by the project.

Derive fluid sizing, maximum widths, wrapping, and breakpoints from supplied variants and existing project behavior. With one design size, implement a conservative adaptation and distinguish it from a designer-specified responsive layout. Test the requested platform; do not create an unrequested desktop or mobile redesign.

For Taro projects that share styles between H5 and mini-program builds, inspect the generated WXSS as well as the source stylesheet. Verify spacing and pressed states on each requested runtime when available.

Enable only relevant behavior branches:

- Navigation: use established destinations and routing behavior.
- Forms and collections: use existing data contracts; implement required validation, loading, empty, error, and success states.
- Tabs and filters: establish state ownership and selection semantics from evidence. Draft/commit behavior applies only when supported.
- Tables: preserve alignment and shown borders; provide overflow appropriate to the target viewport.
- Overlays or sticky UI: read [overlays-and-sticky.md](references/overlays-and-sticky.md).
- Motion or media: reproduce confirmed behavior and handle loading and reduced motion where applicable.

### 4. Verify and iterate

Reuse a suitable running server, or start the documented development command on an available port. Use an available browser automation surface, preferring the in-app browser when suitable, then an authenticated external browser or the project's browser tooling. Inspect the relevant route or existing component preview.

Read [acceptance-checklist.md](references/acceptance-checklist.md) for visual comparison, applicable interaction checks, and completion criteria. Fix large structural differences before local polish. After each change, verify the affected region; perform a final whole-target check.

Run relevant repository checks, inspect the final diff, and distinguish pre-existing failures from introduced ones. Avoid adding dependencies or broad refactors just to perform verification. Preserve pre-existing server sessions and make the state of any server started for this task intentional.

## Recovery and completion

If access or runtime verification fails, inspect the concrete error and try an available relevant alternative. Stop repeating an unchanged failure without new evidence. Continue work that can be completed independently, then report the exact blocker, what was implemented, and what remains unverified. Missing tools or credentials are not evidence of successful verification.

Complete when the requested target is implemented, applicable checks pass, and no known required defect remains. Minor rendering differences may be documented; unresolved layout errors, missing required behavior, or blocked browser checks must not be presented as full completion.

Report concisely:

- implemented target and entry point, including a route only when applicable;
- meaningful behavior and component changes;
- preview location and checks actually performed;
- material assumptions, unresolved differences, or blockers.
