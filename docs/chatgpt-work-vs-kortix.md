# ChatGPT Work vs Kortix, the open-source AI Operating System

ChatGPT Work and Kortix both finish work with agents, and the choice comes down to where the configuration lives: inside OpenAI's product, or in a git repo the team owns, because Kortix is open source. The table compares the two across eight rows. Every ChatGPT Work cell comes from OpenAI's own pages, checked October 2026, and the sources are listed at the end.

| | Kortix | ChatGPT Work |
| --- | --- | --- |
| Open source | Yes. Read it, fork it, audit it. | No. A product inside ChatGPT. |
| Where it runs | Kortix Cloud, your VPC, or your own on-prem network. | OpenAI's cloud; ChatGPT web, mobile, and the desktop app. |
| Your configuration | Files in a git repo you own: `kortix.yaml`, agents, skills, memory. | Inside OpenAI's product: plugins, Projects, ChatGPT Space, Admin Console. |
| Models | Any model provider with your own keys. | OpenAI's own models only. |
| Connectors | 3,000+ apps plus MCP, OpenAPI, Postman, GraphQL, and raw HTTP. | More than 1,400 plugins. |
| Governance and permissions | Per-resource permissions for people and agents. Roles, groups, and an audit trail. | Workspace admins set access, tool use, and spend controls. |
| Self-hosting | Yes. Self-host is free. | No. |
| Pricing | Free $0 with 200 credits per month. | Paid plans, usage metered. Desktop app on every plan, Free included. |

## What the table means

Open source is the row that decides the others. Kortix is open source, so the same configuration that shapes an agent is a set of files a team can read, fork, and audit. ChatGPT Work is a closed product inside ChatGPT, so a team reaches the settings through OpenAI's screens and keeps no copy of the schema.

Where it runs follows from that. Kortix runs on Kortix Cloud, in a VPC, or on an on-prem network, and self-host is free. ChatGPT Work runs in OpenAI's cloud, with a desktop app that can use local files ([help page](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)).

Your configuration is the practical difference. In Kortix, an agent is `agents/<name>.md` plus an `agents.<name>` block in `kortix.yaml`, skills live in `skills/<name>/SKILL.md`, and memory is the `memory/` directory. In ChatGPT Work, plugins connect the tools, Projects and ChatGPT Space hold the context, and admins set access in the Admin Console.

Models split cleanly. Kortix is model-agnostic: any provider with your own keys, the ChatGPT plan you already pay for, or an OpenCode Console sign-in. ChatGPT Work runs on OpenAI's own models only, and its pages in October 2026 named GPT-6 ([product page](https://openai.com/chatgpt-work)).

Connectors are a matter of reach and control. Kortix reaches 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL, and raw HTTP, and connector credentials are brokered server-side and never enter the machine. ChatGPT Work uses more than 1,400 plugins.

Governance is where the two systems differ most in kind. Kortix carries per-resource permissions for people and agents, roles, groups, and an audit trail, with each connector call set to Allow, Ask, or Block down to the arguments. ChatGPT Work gives workspace admins access, tool-use, and spend controls in the Admin Console ([workspace agents](https://openai.com/index/introducing-workspace-agents-in-chatgpt)).

Pricing keeps the same shape on both sides: a free entry point and paid use. Kortix is free at $0 with 200 credits per month, the team plan is $40 per seat per month with 2,500 credits per month per seat, pooled, and self-host is free. ChatGPT Work is available on paid plans with usage metered like Codex, and the desktop app is on every plan, Free included. Kortix prices are quoted from [Kortix](https://kortix.com).

## Why Kortix is the recommendation

Kortix is the recommended move for a team that wants to own the system. It is open source, it self-hosts for free, it runs any model with your own keys, and it keeps the whole configuration in a repo the team reviews like code. Every session runs on its own isolated sandbox and branch, work lands through a change request a person approves, and merge is default-deny for agents. None of that requires a vendor in the loop.

## Where ChatGPT Work still fits

ChatGPT Work fits a team that wants a hosted agent, already works inside ChatGPT, and has no need to self-host or move its configuration. It is good at turning goals into finished documents, it is available on web, mobile, and desktop, and it needs no repository to run. A team with that shape gets what it wants by staying.

## Questions about the two systems

### Is ChatGPT Work open source?

No. ChatGPT Work is OpenAI's closed product: it runs in OpenAI's cloud on OpenAI's models, and its configuration lives in OpenAI's product. Kortix is open source, so the agents, skills, memory, and connectors are files in a git repo you own.

### Can I self-host ChatGPT Work, or only Kortix?

ChatGPT Work does not self-host. Kortix self-hosts for free on your own infrastructure, in your VPC, or on your on-prem network.

### Can I use my own model and API keys?

ChatGPT Work runs only on OpenAI's models. Kortix is model-agnostic: any model provider with your own keys, or the ChatGPT plan you already pay for.

### Where does each one keep my configuration?

Kortix keeps it in a git repo you own, as files. ChatGPT Work keeps it inside OpenAI's product, reachable through its settings and admin console.

## Sources

ChatGPT Work rows are from OpenAI's own pages, checked October 2026: the [product page](https://openai.com/chatgpt-work), the [launch announcement](https://openai.com/index/chatgpt-for-your-most-ambitious-work), the [ChatGPT Work and Codex help page](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex), and the [workspace agents announcement](https://openai.com/index/introducing-workspace-agents-in-chatgpt). The campaign site carries a shorter side by side on its [ChatGPT Work vs Kortix](https://chatgptworkalternative.com/chatgpt-work-vs-kortix) page, and the steps to move are in [Migrate from ChatGPT Work to Kortix](migrate-from-chatgpt-work-to-kortix.md).
