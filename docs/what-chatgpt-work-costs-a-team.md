# What ChatGPT Work costs a team, and what the open-source route costs

ChatGPT Work's cheapest real team bill is $40 a month before a single agent runs anything, and that bill rents a closed system. Kortix is the open-source AI Operating System, and the route it opens starts at $0: the same kind of agent work, run from a git repo you own, with the configuration as files you can read and version. Every number below comes from OpenAI's or Kortix's own published prices.

## What ChatGPT Work charges

ChatGPT Work runs inside a ChatGPT workspace, and every ChatGPT Business workspace carries at least two seats ([ChatGPT Business overview](https://help.openai.com/en/articles/8792828-chatgpt-business-overview)). Business Standard costs $20 per seat billed annually or $25 month to month; Business Premium costs $100 or $125 on the same terms ([ChatGPT pricing](https://chatgpt.com/pricing)). Two seats are therefore the floor: $40 a month on annual billing, $480 a year, or $50 a month and $600 a year on monthly billing.

The seat prices are recent. OpenAI cut Business Standard from $25 and $30 to $20 and $25 on April 2, 2026 ([ChatGPT pricing](https://chatgpt.com/pricing)). The seat bill is also only the entry price. Work's usage works like Codex, so a heavier task consumes more of the plan's included usage, and metered usage lands on top ([ChatGPT Work and Codex](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)).

For a five-person team the arithmetic is simple. Five seats on Business Standard annual come to $100 a month, $1,200 a year, before any agent has run a task.

What the rent buys is worth naming, because it shapes what the money cannot do. The models are OpenAI's own: GPT-6 Astra has run in ChatGPT Work since September 9, 2026, on every plan from Plus up ([ChatGPT Work and Codex](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)). You cannot point one agent at a cheaper provider and another at a stronger one; the model choice belongs to the plan. The configuration lives in OpenAI's product as well, so the instructions and tool rules a team builds cannot be diffed, versioned or exported the way code can. The code itself is closed.

## What the open-source route costs

Kortix is open source. Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free ([Kortix](https://kortix.com)). The models are any model provider with your own keys, so the platform itself costs nothing and the model spend is whatever your provider charges.

On the managed cloud, free is $0 with 200 credits per month and 1 project. Paid plans start at $50 a month for 5,000 credits, and members are free, sharing one credit pool ([Kortix pricing](https://kortix.com/pricing)). Members being free is the part that changes team math: five people draw on one pool, and nobody pays per head.

The configuration is where the route differs in kind. Agents, skills, memory, connectors and schedules are files in one git repo. The open-source ChatGPT Work alternative starter ships one a team can run:

```yaml
# yaml-language-server: $schema=https://kortix.com/schema/kortix.v2.schema.json
#
# Kortix starter: an open source ChatGPT Work alternative you can run.
kortix_version: 2

default_agent: assistant

project:
  name: chatgpt-work-starter
  description: Open source Kortix starter with one role agent, one skill and a memory folder.

env:
  optional:
    - OPENAI_API_KEY
    - ANTHROPIC_API_KEY
    - DAYTONA_API_KEY

runtime: opencode

agents:
  assistant:
    file: agents/assistant.md
    skills:
      - weekly-report
    # Memory is a folder in this repo: memory/. Agents read it and append to it.
    workspace: branch

# Connectors, triggers and sandbox templates are left out of this starter.
# Add them as the project needs them; see the Kortix docs.
```

That file is the cost story in miniature. The agent is a Markdown file, the skill it loads sits beside it, and the provider keys are declared but optional, so a team can start on an OpenAI or Anthropic key it already holds and keep it.

## The two cost shapes side by side

| Cost line | Kortix | ChatGPT Work (Business) |
|---|---|---|
| Platform entry | $0 self-hosted, or $0 with 200 credits a month | Two seats minimum, from $20 a seat |
| Smallest team bill | $0 self-hosted; $50 a month managed | $40 a month annual, $50 monthly |
| Five-person team | $0 self-hosted; $50 a month, one shared pool | $100 a month annual, $1,200 a year |
| Extra spend | Your model provider, billed directly | Usage metered like Codex |
| Configuration | Files in a git repo you own | Inside OpenAI's product |
| Code | Open source, auditable | Closed |

Prices are each vendor's own published rate, checked October 2026: [ChatGPT pricing](https://chatgpt.com/pricing), [ChatGPT Business overview](https://help.openai.com/en/articles/8792828-chatgpt-business-overview), [Kortix pricing](https://kortix.com/pricing).

## Which bill scales better

Seat pricing scales with headcount and metered usage scales with ambition, and both land on the invoice OpenAI sends. The open-source route concentrates spend where a team can see it: the model provider it already chose. The five-person team on Business Standard pays $1,200 a year in rent before usage; the same five on self-hosted Kortix pay their model provider directly and $0 for the platform, or from $50 a month on managed credits shared across everyone.

The rent also buys less control per dollar: closed code, fixed models, configuration in someone else's product. The repo buys the opposite, and the files travel with you, because the same manifest that runs on a laptop runs in your VPC.

## Move the work

The move is a rebuild, one job at a time, and the steps are short: [Migrate from ChatGPT Work to Kortix](migrate-from-chatgpt-work-to-kortix.md) walks the inventory, the ordered steps and the mapping from every ChatGPT Work asset to a file in the repo. For the current managed-cloud numbers in their shorter consumer form, see the [pricing page](https://chatgptworkalternative.com/pricing).
