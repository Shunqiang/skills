# Design Evidence

Read while gathering or refreshing evidence. Scale inspection to the requested scope.

## Collect progressively

1. Confirm the file, target node, node type, dimensions, and screenshot. For long pages inspect the full target, not only its first viewport.
2. Identify section boundaries, shared components, variants, and relevant prototype states. Inspect detailed metadata only for subtrees that need it.
3. Capture layout constraints, spacing, typography, colors, borders, radii, shadows, and asset references needed for implementation.
4. Inspect existing component mappings and project tokens before creating replacements. Confirm that a candidate component can support the required appearance and behavior without unrelated global changes.

If a response is truncated, narrow the target to relevant children rather than treating the partial response as complete. If a tool returns generated code, adapt it to the repository instead of treating its framework choices or coordinates as architectural requirements.

## Interpret sources by purpose

- Use design properties and constraints for measurements; screenshots for rendered composition and visual validation.
- Use prototypes, explicit requirements, and existing product contracts for interaction behavior.
- Use repository conventions for implementation architecture and data integration.
- Treat a screenshot-only measurement as an estimate. A static screenshot does not establish scrolling, sticky behavior, breakpoints, or submission semantics.
- If sources conflict, inspect the selected state and context. Resolve inconsequential differences conservatively; surface conflicts affecting requested behavior or visual output.

## Working summary

Keep only information that avoids repeated calls or guides implementation:

- target identity, dimensions, and inspected states;
- relevant project files, components, fonts, and tokens;
- module layout rules and confirmed responsive variants;
- asset-to-element mapping and durable asset locations;
- confirmed interactions, material inferences, and unresolved questions.

Refresh evidence when the target, design, or relevant project code changes. Reuse it otherwise. Do not read every sibling frame or enumerate every layer without a concrete need.
