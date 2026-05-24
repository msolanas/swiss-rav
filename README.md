# Swiss RAV Assistant — Claude Code Plugin

A Claude Code plugin for Swiss job seekers managing their RAV obligations. Automates job-room.ch interactions via browser control, tailored to your specific canton and ALK.

> **Requires:** Playwright MCP — see Prerequisites below.

## Commands

| Command | What it does |
|---|---|
| `/rav:setup` | One-time setup — run this first |
| `/rav:status` | Full RAV status overview and upcoming deadlines |
| `/rav:work-effort` | Log a job application to job-room.ch |
| `/rav:avp` | Submit your monthly AvP (Angaben der versicherten Person) declaration |
| `/rav:incapacity` | Report illness or accident |
| `/rav:unemployment` | Manage your ALE-Antrag (benefit application) |
| `/rav:upload-doc` | Upload a document to RAV |
| `/rav:unia-contact` | Contact your Unia ALK branch via their web form |
| `/rav:pension-buyin` | Guide for severance/pension buy-in (high severance situations) |

## Prerequisites

### 1. Playwright MCP

Every command except `/rav:pension-buyin` uses browser automation — most drive job-room.ch, and the contact commands drive your ALK's web form. You need a browser MCP installed in Claude Code.

Install the Playwright MCP by adding it to your Claude Code MCP config:

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    }
  }
}
```

### 2. job-room.ch account

You need an active account at [job-room.ch](https://www.job-room.ch). Your RAV counsellor will set this up when you register.

## Installation

Inside Claude Code, run:

```
/plugin marketplace add msolanas/swiss-rav
/plugin install rav@msolanas
```

## Setup

Run `/rav:setup` once after installing — it configures your profile and checks where you stand with RAV.

### When to run it

Run it **after you've registered as unemployed and have a job-room.ch login** (your RAV counsellor sets up the account when you register). You don't need to have finished your benefit application or uploaded any documents first — setup will check what's still outstanding and tell you. In short: as soon as you can log into job-room.ch, run `/rav:setup`.

### What it asks you

It asks a few questions, one at a time, then reads them back for you to confirm before saving:

- **Personal details:** first name, last name, email, phone, postcode, city
- **RAV details:** your canton, your agreed monthly application quota (often 10–12), and your `Arbeitslosenkasse (ALK / unemployment fund)` — Unia, SYNA, Kantonal, or other
- **Career-ops tracker** (optional): link it if you use one, or skip

You don't enter your ALK branch address or canton rules — setup **researches** those from your canton/postcode and shows them to you to confirm or correct.

### What it does

1. Checks your browser MCP is working
2. Collects and **confirms** your personal + RAV details (with basic format validation)
3. Researches and confirms your ALK branch (address, phone, contact form, hours)
4. Researches canton-specific RAV rules (deadlines, AvP window, pacing)
5. Writes `~/.rav/config.json` and `~/.rav/context.md` (these stay on your machine, never uploaded)
6. **Checks job-room.ch for unfinished onboarding** — your `ALE-Antrag (benefit application)`, document uploads, and AvP — and ends with either *"you're fully RAV-ready"* or a concrete list of actions still to take, each linked to the command that handles it

Re-running `/rav:setup` is safe — it overwrites your config and re-checks your readiness.

## Career-ops integration

If you use [career-ops](https://github.com/santifer/career-ops) for application tracking, `/rav:setup` can link it. The `/rav:work-effort` command will then sync logged entries automatically (always optional).

## Important: save approval rule

Every command that writes to job-room.ch will **always show you a summary and wait for your explicit confirmation** before clicking Save or Submit. This rule cannot be bypassed.

## Privacy & safety

- **Your data stays local.** Your personal profile lives only in `~/.rav/config.json` and `~/.rav/context.md` on your machine. Your data is only transmitted to Claude, hence Anthropic as part of your conversations — the plugin only submits to the official job-room.ch / ALK forms you explicitly approve.
- **It uses your own logged-in session.** Browser automation acts as you, in your browser, against job-room.ch. It never asks for or stores your password.
- **You approve every submission** (see the save-approval rule above).
- **Sensitive IDs stay yours.** The plugin never auto-fills your `AHV-Nummer (social-security number)` — you enter it yourself.
- **Not legal, tax, or financial advice.** Commands like `/rav:pension-buyin` summarise public rules to help you act, but thresholds and laws change — verify current figures with your ALK, RAV counsellor, or a professional before deciding. No warranty; use at your own risk.
- **Security issues:** see [SECURITY.md](SECURITY.md) for private disclosure.

## License

MIT
