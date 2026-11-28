# Privacy

This file says what each skill in this pack sends, to which host, and when.

## bsv-facts

bsv-facts has no scripts. It never asks for a seed phrase, a private key or personal data. It keeps no record of your requests.

**When it sends anything.** To answer a question, the agent reads the matching page on bitcoinsv.it.

**How.** The agent makes the request with its own web tool. Each request is a plain GET for a public page. It carries no BSV address, transaction ID, Paymail handle or other personal data, and no API key.

**Where.** Only bitcoinsv.it. The agent does not follow a page's links to other sites; it gives them to you instead.

**What the site sees.** bitcoinsv.it sees the IP address of the machine that makes the request and the page asked for. That machine is your computer, or your AI provider's servers when the agent's web tool runs there. The site's own privacy policy is at https://bitcoinsv.it/privacy/.

## paymail-lookup

paymail-lookup has no scripts. It never asks for a seed phrase or a private key, and it uses only the handle you ask it to check. It keeps no record of your requests.

**When it sends anything.** Only when you ask it to check a Paymail handle.

**How.** The agent makes plain GET requests with its own web tool. It never asks a server for a payment address, and it never pays.

**Where.**

| Host | What the agent reads there |
|---|---|
| dns.google | Which server answers Paymail for the handle's domain |
| The Paymail server for that domain | Its list of services, the handle's public key and display name, whether the server says that key belongs to the handle, and the same key lookup for one made-up name |

The agent reads nothing on any other host. If the server's list of services points to another host, or a reply redirects there, the agent does not follow it and tells you.

**What those hosts see.** Google sees the domain being checked. The Paymail server sees the handle being checked. Both see the IP address of the machine that makes the request: your computer, or your AI provider's servers when the agent's web tool runs there.

## bsv-whale-watch

bsv-whale-watch has no scripts. It never asks for a seed phrase or a private key. It keeps no record of your requests.

**When it sends anything.** When you ask about the largest BSV holders or about one address.

**How.** The agent makes plain GET requests with its own web tool, with no API key. Before the first explorer read, it tells you the addresses will go to a public explorer.

**Where.**

| Host | What the agent reads there |
|---|---|
| bitcoinsv.it | The rich list page and its label list. No user data. |
| raw.githubusercontent.com (GitHub) | The weekly snapshot files, their README and the last-move file. No user data. |
| api.whatsonchain.com | The balance and history of each address checked, and block times |
| api.bitails.io | The same address reads, only when WhatsOnChain does not answer |

**What those hosts see.** bitcoinsv.it and GitHub see only which public files were read. WhatsOnChain, or Bitails, sees the addresses checked. All of them see the IP address of the machine that makes the request: your computer, or your AI provider's servers when the agent's web tool runs there.

## Every skill in this pack

- A skill sends nothing when it is installed. The tool you install it with, such as the skills CLI or Claude Code, follows its own terms.
- The skills have no telemetry.
- The skills store nothing.

## Contact

For questions about this file, write to contact@bitcoinsv.it.
