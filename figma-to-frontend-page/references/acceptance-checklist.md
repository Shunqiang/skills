# Figma Frontend Acceptance Checklist

Use before completion. Apply only sections relevant to the requested target and confirmed requirements. Do not add UI, routes, states, or platform support merely to satisfy this checklist.

## Reproducible visual comparison

- Confirm the reference is the selected node and intended state.
- Match the browser's CSS viewport to the reference dimensions. For long designs, match width and compare equivalent scroll regions or full-page captures; do not confuse total frame height with a required viewport height.
- Wait for fonts and images to load. Use stable content and a controlled animation state for comparison.
- Compare the full requested target, including below-the-fold content. For a local edit, also check affected surrounding layout.
- Fix differences in this order: missing content and overall geometry; fonts and wrapping; assets and spacing; colors, borders, shadows, and small details.
- Use overlays or image diffs when available and useful. Do not rely on one pixel-difference percentage: antialiasing and dynamic content can produce noise.
- Check applicable nearby widths for overflow and wrapping. Verify supplied responsive variants at their target widths; identify adaptations inferred from a single design.

## Architecture and assets

- [ ] Destination files match the target type and repository conventions.
- [ ] Routes are preserved or added only when needed, following existing patterns without conflicts.
- [ ] Existing suitable components, mappings, tokens, and assets were reused.
- [ ] Component boundaries have a responsibility, reuse, or complexity rationale.
- [ ] Layout uses flow, flex, or grid except where overlap requires positioning.
- [ ] Item spacing uses explicit class-based margins; no `gap` or universal/sibling spacing selectors were introduced. Applicable WXSS output and fixed overlays use supported CSS declarations.
- [ ] Fonts, icons, and images load correctly from project-supported locations.
- [ ] No missing sections, unintended clipping, overlap, or substantial layout shifts remain.

## Applicable behavior

- [ ] Navigation uses confirmed destinations and works from the expected entry point.
- [ ] Controls have appropriate semantics, names, keyboard operation, and visible focus.
- [ ] Tabs and filters implement the confirmed selection and state boundaries.
- [ ] Forms use established validation and submission contracts; success is not faked.
- [ ] Required loading, empty, error, disabled, and success states were exercised.
- [ ] Tables preserve header/body alignment, shown borders, and appropriate overflow.
- [ ] Overlays and sticky UI pass the applicable checks in overlays-and-sticky.md.
- [ ] Media and meaningful motion handle required loading, fallback, and reduced-motion behavior.

## Verification and completion

- [ ] The target was opened and inspected in a real browser.
- [ ] Screenshot comparison was performed at the intended viewport and state.
- [ ] Required interactions were exercised and new target-specific browser errors checked.
- [ ] Relevant typecheck, lint, tests, or build ran as appropriate to repository requirements and the change.
- [ ] Final diff was inspected for unrelated edits and preservation of existing user work.
- [ ] Any server started by this task is left in an intentional state; pre-existing sessions are preserved.
- [ ] Material assumptions and unresolved differences are recorded in the completion report.

Completion requires the requested implementation and applicable verification, with no known required defect left. Distinguish acceptable small rendering differences from missing behavior or structural mismatches. If tooling, credentials, or an existing environment failure prevents a check, report partial completion and the blocked check explicitly.
