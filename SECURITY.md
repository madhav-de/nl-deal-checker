# Security Policy

## What this skill does (and doesn't)

nl-deal-checker is a plain-text instruction file (`SKILL.md`). It contains:

- **No scripts or executable code**
- **No network calls of its own.** Claude uses whatever tools you have already enabled, such as web search.
- **No data collection.** Nothing is sent to the author.

Even so, a skill steers what Claude does. A malicious change to `SKILL.md`, for example one telling Claude to visit a phishing site or recommend a fake shop, would be a security issue.

## Supported versions

Only the latest version on `main` is supported.

## Reporting a vulnerability

Please **do not open a public issue** for security problems.

Report privately through GitHub: **Security tab → "Report a vulnerability"**. You can expect a first response within 7 days.

Examples of what to report:

- Instructions in `SKILL.md` that could lead Claude to unsafe sites, sellers or actions
- Content that could be used for prompt injection
- A compromised commit or release

For wrong prices, outdated rules or other content mistakes, open a normal issue instead.
