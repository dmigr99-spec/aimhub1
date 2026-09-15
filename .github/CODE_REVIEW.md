# AI review setup

This repository uses two independent pull-request reviewers:

- Codex: repository review guidance is in `AGENTS.md`. Enable Codex Code Review for this repository in the Codex GitHub integration.
- Claude: repository guidance is in `CLAUDE.md`. `.github/workflows/claude-code-review.yml` runs on non-draft pull requests.

## GitHub authentication

Claude review uses Octo STS to mint a short-lived GitHub token rather than a PAT. The trust policy is `.github/chainguard/claude-review.sts.yaml` and grants only:

- `contents: read`
- `pull_requests: write`
- `issues: write`

The workflow itself only receives `contents: read` and `id-token: write`; PR write permissions come from the short-lived Octo STS token.

Install the Octo STS GitHub App on `dmigr99-spec/aimhub1` before running the workflow.

## Anthropic authentication

The workflow currently expects the repository Actions secret `ANTHROPIC_API_KEY`. Prefer Anthropic Workload Identity Federation later if your Anthropic account supports it, which removes the long-lived API secret as well.

## Safety

The review workflow does not grant repository-content write access. It can read code and write PR/issue review feedback only.
