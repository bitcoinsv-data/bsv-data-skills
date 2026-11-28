# BSV Data Skills

Agent skills for Bitcoin SV (BSV). They help an AI agent answer BSV questions from current pages, check Paymail handles and follow the largest BSV holders with live data, instead of relying on out-of-date memory. They never ask for a seed phrase or private key. They never move funds.

## Skills

| Skill | What it does |
|---|---|
| `bsv-facts` | Answers general questions about BSV by reading the matching page on bitcoinsv.it, and gives the link. |
| `paymail-lookup` | Checks a BSV Paymail handle before you pay it: whether it exists, its server, its public key and warning signs. It only reads public data. |
| `bsv-whale-watch` | Follows the 100 largest BSV addresses: who holds them when that is proven, which belong to exchanges, how their balances change week to week, and when dormant coins move. It gives no trading advice. |

## Install

For Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI and other agents that read skills:

    npx skills add bitcoinsv-data/bsv-data-skills

To install one skill by name:

    npx skills add bitcoinsv-data/bsv-data-skills --skill bsv-facts
    npx skills add bitcoinsv-data/bsv-data-skills --skill paymail-lookup
    npx skills add bitcoinsv-data/bsv-data-skills --skill bsv-whale-watch

Skills go into the current project by default. Add `-g` to install them for all your projects. The `npx skills` commands need Node.js.

As a Claude Code plugin:

    /plugin marketplace add bitcoinsv-data/bsv-data-skills
    /plugin install bsv-data-skills@bsv-data

## What the skills send

The skills have no scripts. The agent makes every request with its own web tool.

- `bsv-facts` reads the matching public page on bitcoinsv.it. The request carries no BSV address, transaction ID or other personal data.
- `paymail-lookup` asks Google's public DNS about the handle's domain, then reads the domain's Paymail server. Google sees the domain, and the Paymail server sees the handle. It never asks a server for a payment address.
- `bsv-whale-watch` reads the rich list and its label list on bitcoinsv.it and the weekly snapshot files on GitHub. When you ask about one address, it reads that address on WhatsOnChain, or on Bitails if WhatsOnChain does not answer. Those explorers see the addresses checked.

The skills send nothing at install time. They keep no record of your requests. Each skill needs internet access and an agent with a web fetch tool. Details are in PRIVACY.md.

## Keeping facts current

The facts live on the bitcoinsv.it pages, and they are kept current there. bsv-facts only says which page answers which kind of question, so an installed copy reads the current page each time. A new version of the skill comes out when a page moves or a new page is added.

To update skills installed with `npx skills`:

    npx skills update

To update the Claude Code plugin, refresh the marketplace first:

    claude plugin marketplace update bsv-data
    claude plugin update bsv-data-skills@bsv-data

To report an outdated fact or a broken link, open an issue in this repository.

## License and security

Apache License 2.0. Copyright 2026 BSV Data. See LICENSE and NOTICE. To report a security problem, see SECURITY.md.

Made by BSV Data (bitcoinsv.it), an independent site about Bitcoin SV (BSV).
