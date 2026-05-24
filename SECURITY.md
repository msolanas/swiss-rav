# Security Policy

## Scope

Swiss RAV Assistant is a Claude Code plugin made of markdown command files. It has no server, no bundled binaries, and ships no user data. At runtime it:

- drives a browser MCP (Playwright) against your own logged-in **job-room.ch** session,
- reads and writes **only** your local `~/.rav/config.json` and `~/.rav/context.md`,
- runs small embedded Python snippets that touch those local files and (optionally) your local career-ops tracker.

It never transmits your data anywhere except the official job-room.ch forms you explicitly approve.

## Reporting a vulnerability

Please report security issues **privately**, not in a public issue:

- Use GitHub's **[Report a vulnerability](https://github.com/msolanas/swiss-rav/security/advisories/new)** (Security → Advisories), or
- open a minimal public issue asking for a private contact channel (no details).

Include: the command involved, what happens, and why it's a risk. We aim to acknowledge within a week.

## What counts as a vulnerability here

Because this is a prompt/automation plugin, the relevant risks are different from a typical app:

- A command that **writes or submits to job-room.ch without the explicit save-approval step** (the approval gate is a hard safety contract — bypassing it is a security bug).
- A command that **auto-fills a sensitive government ID** (e.g. the `AHV-Nummer` / social-security number) instead of leaving it for the user.
- Any instruction that causes a command to **exfiltrate local data** (`~/.rav`, credentials, browser cookies) to a third party.
- **Prompt-injection** paths where untrusted page content or a crafted document could redirect a command's behavior.
- Hardcoded **secrets or personal data** committed to the repo.

## Out of scope

- Vulnerabilities in job-room.ch / arbeit.swiss itself (report those to SECO/the operator).
- Vulnerabilities in the Playwright MCP or Claude Code (report upstream).
- Your local machine security (file permissions on `~/.rav/`, etc.).

## Good practice for users

- Keep `~/.rav/` private; it contains your personal RAV profile.
- Review every summary before approving a Save/Submit.
- Only install ALK contact commands you've read.
