# Security

This ecosystem records host metrics and decision traces. It must not record secrets or personal data.

## Report

Email the owner via GitHub: [mfathialrahman-crypto](https://github.com/mfathialrahman-crypto).

Do not open a public issue for a live credential leak.

## Rules

- No API keys, tokens, or `.env` files in git.
- Signatures are truncated SHA-256 of public snapshots, not auth.
- GitHub Actions should use repository permissions already granted to `GITHUB_TOKEN`.
