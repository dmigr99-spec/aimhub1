# Automation security notes

AI review automation uses least-privilege, short-lived GitHub credentials via Octo STS. Security-sensitive workflow and trust-policy files are owned through `.github/CODEOWNERS`.

Third-party GitHub Actions are pinned to immutable commit SHAs. Review workflows receive only the permissions required to read repository contents, request an OIDC token, and post review feedback through the short-lived federated token.
