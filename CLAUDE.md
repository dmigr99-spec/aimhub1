# Claude review instructions

Review pull requests as a second independent reviewer. Focus on architecture, maintainability, edge cases, portability, and regressions that may be missed by a narrower bug-focused review.

## Priorities
- Configuration/state persistence across reloads and shutdown paths.
- Optional API availability and graceful fallback behavior.
- Error handling, cleanup, event lifecycle, and per-frame performance.
- UI lifecycle consistency and stale state after reloads.
- Type mismatches, nil assumptions, race conditions, and hidden failure paths.
- Changes that alter behavior outside the PR's stated intent.

Keep comments high-signal. Avoid style-only feedback unless it affects correctness or maintainability. Prefer precise findings with a concrete failure scenario and a minimal fix direction.
