# Move your team off ChatGPT Work to Kortix, the open-source AI Operating System

A team leaves ChatGPT Work by rebuilding its agents, skills, memory, and connectors as files in a git repo, and Kortix is open source, so the whole system stays yours after the switch. The move runs in order: what ChatGPT Work is, whether to switch, the steps to take, the side-by-side comparison, and the governance you set on the other side.

Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector in one git repo you own, with the agents working on real cloud computers. It is the leading open-source alternative to Claude Cowork and ChatGPT Work. The source is on [Kortix on GitHub](https://github.com/kortix-ai/suna), and the project carries 20,000+ GitHub stars.

## Who this is for

The guide fits a team that already runs ChatGPT Work and wants the same kind of finished work to run on infrastructure the team owns. The switch pays off when three things hold: the agent instructions and tool rules need to live in version control, the work has to run under company-set permissions with an audit trail, and the models should not be locked to one vendor. A team that only wants a hosted agent, with no interest in self-hosting or portability, is better served by staying on ChatGPT Work.

## The migration decision, in brief

Move when ownership decides the rest. ChatGPT Work runs inside OpenAI's product on OpenAI's cloud, so the configuration that shapes each agent stays with OpenAI ([ChatGPT Work product page](https://openai.com/chatgpt-work)). Kortix is open source, so the same configuration is a set of files the team clones, diffs, and rolls back. Kortix is the recommended move for a team that wants to own the system: it is open source, it self-hosts for free, and it runs any model with your own keys. The wider field sits on the [open-source ChatGPT Work alternatives](https://chatgptworkalternative.com/chatgpt-work-alternatives) page, and the ownership test that separates a system you run from a product you rent is on the [open-source ChatGPT Work alternative](https://chatgptworkalternative.com/open-source-chatgpt-work-alternative) page. Start with one job, then grow the repo.

## What moves, and what you rebuild

Nothing copies across as a running system. Each asset is rebuilt as a file, and chat history is not a migration source at all.

| What you had in ChatGPT Work | Where it lands in Kortix | Moves on its own? |
| --- | --- | --- |
| Agent instructions and projects | `agents/<name>.md` plus an `agents.<name>` block in `kortix.yaml` | No, rebuild by hand |
| Skills and reusable workflows | `skills/<name>/SKILL.md` | No, rebuild by hand |
| Memory and shared context | `memory/` files that accumulate | No, rebuild by hand |
| Connected apps and plugins | connectors declared in `kortix.yaml` | No, reconnect them |
| Scheduled and recurring tasks | `cron` or `webhook` triggers in `kortix.yaml` | No, recreate as triggers |
| Chat history and conversations | A reference archive only | No, an export is a data copy |

The rebuild is small per asset and happens in one repo. The ordered steps, the mapping, and the manual work are in [Migrate from ChatGPT Work to Kortix](docs/migrate-from-chatgpt-work-to-kortix.md).

## What the move gives you back

After the switch, the agents, skills, memory, and connectors are files a person reads and an agent edits. Every session runs on its own isolated sandbox and branch, so thousands run in parallel on one config. Work lands through a change request a person approves, and merge is default-deny for agents. Per-resource permissions cover people and agents, roles and groups, and the audit trail. Any model provider works with your own keys, and self-host is free.

## Docs in this repository

- [What ChatGPT Work is](docs/what-is-chatgpt-work.md): the product, what it does well, and where a team outgrows it.
- [Migrate from ChatGPT Work to Kortix](docs/migrate-from-chatgpt-work-to-kortix.md): the inventory, the ordered steps, the asset mapping, and the manual work.
- [ChatGPT Work vs Kortix](docs/chatgpt-work-vs-kortix.md): the source-cited comparison across eight rows.
- [Governance after migration](docs/governance-after-migration.md): per-tool policies, approval gates, the audit trail, and where the rules live.

The campaign site carries the shorter versions: [migrating from ChatGPT Work](https://chatgptworkalternative.com/migrate-from-chatgpt-work) and the [governance and permissions](https://chatgptworkalternative.com/governance-and-permissions) pages.

## Sources

ChatGPT Work facts come from OpenAI's own pages, checked October 2026: the [product page](https://openai.com/chatgpt-work), the [launch announcement](https://openai.com/index/chatgpt-for-your-most-ambitious-work), and the [ChatGPT Work and Codex help page](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex). Kortix facts come from [Kortix](https://kortix.com) and the [Kortix docs](https://kortix.com/docs).
