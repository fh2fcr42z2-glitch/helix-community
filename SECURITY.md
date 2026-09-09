# Security

This repository is **public documentation**. It must never contain API keys, tokens, cookies, wallet seeds, or private helix-cx source.

## If you find a secret

1. **Do not** paste it into an issue, a comment, a PR, or a screenshot.
2. **Do not** clone the leak into a gist “for reference.”
3. Prefer GitHub **private vulnerability reporting** on this repo (Security → Advisories → Report) if it is enabled.
4. If that path is missing, open a **minimal** issue titled `security: credential leak` with:
   - where it appeared (commit SHA, file path, CI log URL)
   - **no** secret value
5. If the secret is *your* key that you almost committed, rotate it at the vendor first, then tell us the name of the variable — not the value.

## What counts as a secret here

- API keys and demo keys that still authenticate
- Exchange passwords, API passphrases, 2FA backup codes
- Wallet seeds, private keys, session cookies
- `.env` contents, HAR files, vendor dashboard URLs that embed tokens
- Anything copied out of the private [helix-cx](https://github.com/fh2fcr42z2-glitch/helix-cx) tree that was not meant for public docs

## What we will never ask for

Maintainers will not ask you to send a live key, a seed, or a dump of helix-cx. See [docs/SENSITIVE-INTEGRATIONS.md](docs/SENSITIVE-INTEGRATIONS.md).

## Scope

This policy covers **this public repo**. It is not a bounty program and not a live-trading incident response plan.
