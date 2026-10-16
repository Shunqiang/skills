# Overlays and Sticky UI

Read only when the requested target includes confirmed overlay, fixed, or sticky behavior.

## Implementation decisions

- Prefer the repository's established overlay primitives, portal convention, focus handling, and scroll-lock mechanism.
- Determine the actual scroll container and sticky containing block. Check ancestor overflow and transforms when positioning behaves unexpectedly.
- Use a shared source for CSS positioning and JavaScript scroll offsets. Measure runtime dimensions when headers vary or unit conversion makes source values unreliable; stable existing layout tokens do not require new measurement machinery.
- Define stacking relationships among navigation, sticky controls, panels, masks, and content. Keep local stacking contexts in mind rather than increasing z-index blindly.
- Preserve intended panel scrolling while preventing background scrolling only when modal behavior requires it. Choose the project's compatible method; do not universally prescribe body positioning or wheel/touch event cancellation.
- Provide focus entry and restoration, keyboard dismissal, and focus containment where modal semantics require them. Mask dismissal follows the confirmed product behavior.
- For filters with an established draft/commit flow, Cancel discards draft changes and Confirm commits them. Do not introduce this flow for immediate-apply filters.

## Verify applicable paths

- Open and close through supported controls, keyboard actions, and mask actions.
- Confirm intended mask coverage, stacking, panel overflow, and background scroll behavior.
- Close while scrolled and check restoration without a jump or stranded scroll lock.
- Verify tab order and focus restoration to the triggering control.
- When an overlay is attached to a sticky region, test opening both before and after the sticky threshold.
- If content or header dimensions change, check that offsets remain correct.
