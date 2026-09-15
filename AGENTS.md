# Repository review instructions

This repository contains Lua/Luau scripts. When reviewing pull requests, focus on high-signal defects that can cause incorrect behavior, crashes, lost configuration, broken portability, resource leaks, stale state, or regressions.

## Review priorities
- Verify state/configuration persistence and hot-reload behavior.
- Check compatibility guards around optional runtime APIs and services.
- Check nil handling, type checks, pcall/error handling, and cleanup paths.
- Check event/render-loop lifecycle and avoid duplicate bindings or stale connections.
- Check UI teardown/recreation behavior and saved-state restoration.
- Flag performance problems inside per-frame or frequently-called code.
- Prefer concrete, reproducible findings over style-only comments.
- Do not suggest broad rewrites when a small fix is sufficient.
- When possible, explain the failure mode and point to the exact changed lines.

Treat correctness and regressions as higher priority than formatting or naming preferences.
