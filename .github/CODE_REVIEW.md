# AI review setup

This repository is prepared for two independent pull-request reviewers:

- Codex: repository instructions live in `AGENTS.md`. Enable Codex Code Review for this repository in Codex/GitHub so PRs are reviewed automatically; `@codex review` can also be used on a PR.
- Claude: repository instructions live in `CLAUDE.md`. The workflow in `.github/workflows/claude-code-review.yml` runs on non-draft pull requests and posts review findings to the PR.

## Claude authentication required

Before the Claude workflow can succeed, install the official Claude GitHub App for this repository and add an Actions secret named `ANTHROPIC_API_KEY` (or adapt the workflow to use `CLAUDE_CODE_OAUTH_TOKEN`).

The workflow is intentionally review-focused and does not grant the job write access to repository contents.
