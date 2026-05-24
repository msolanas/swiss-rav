# Contributing to Swiss RAV Assistant

Contributions are welcome! This plugin helps Swiss job seekers navigate RAV obligations — if you have improvements, bug fixes, or support for additional ALKs, please open a PR.

## Ways to contribute

- **Bug fixes** — something broken on job-room.ch? Open an issue with steps to reproduce.
- **New ALK support** — add a new `commands/alk-<name>.md` for your ALK's contact workflow.
- **Canton-specific improvements** — if the setup research misses something for your canton, submit a fix.
- **Translations** — the commands are in English with German form content. Improvements welcome.

## How to submit a PR

1. Fork the repo
2. Create a branch: `git checkout -b feat/my-improvement`
3. Make your changes to the relevant `commands/*.md` file
4. Test manually by invoking the command in Claude Code
5. Open a PR with a clear description of what changed and why

## Guidelines

- Command files are markdown — keep instructions clear and unambiguous
- Never hardcode personal data (names, addresses, phone numbers) — use `~/.rav/config.json` reads
- The save-approval rule is non-negotiable: never submit to job-room.ch without explicit user confirmation
- Test with at least one real ALK or canton before submitting canton-specific changes
- Read [CLAUDE.md](CLAUDE.md) first — it covers the architecture invariants, plugin best practices, the save-approval and untrusted-content rules, and the data-boundary (no-PII) rule every command must follow

## Reporting issues

Open a GitHub issue at https://github.com/msolanas/swiss-rav/issues. Include:
- Which command failed
- What you expected to happen
- What actually happened
- Your canton and ALK (helps diagnose canton-specific issues)
