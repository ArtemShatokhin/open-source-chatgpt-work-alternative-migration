# Migrate from ChatGPT Work to Kortix, the open-source AI Operating System

Migrating from ChatGPT Work to Kortix means rebuilding the agents, skills, memory, connectors, and schedules as files, because Kortix is open source and reads a git repo instead of an OpenAI workspace. Nothing imports as a running system: each asset is written once as a file, then shipped in one command. The move has an inventory, ten ordered steps, a mapping between the two systems, and a set of manual tasks.

## Step 1: Inventory the work running on ChatGPT Work

List what actually runs before rebuilding anything, so the move has a scope. In ChatGPT, check five places.

- The Agents tab, for the workspace agents the team built or shares.
- Projects, for the instructions, files, and context that group each body of work.
- Scheduled, for tasks that run once, on a schedule, or when an event fires.
- The plugins directory and workspace settings, for the tools an agent may reach.
- Settings, for custom instructions and saved memory.

For each agent, write down three things: the job it does, the tools it touches, and the schedule it runs on. That list is the migration plan, and it is why starting with one job works better than moving the whole workspace at once.

## Step 2: Export what OpenAI will give you, and know its limits

OpenAI's export is a copy of account data, not a package another platform can import. Request it in ChatGPT under Settings, Data controls, Export data, or through OpenAI's Privacy Portal. OpenAI's help says an export can take up to 7 days to arrive and the download link expires 24 hours later ([export help](https://help.openai.com/en/articles/7260999-exporting-your-chatgpt-history-and-data)). Self-service export is not available in ChatGPT Business or Enterprise workspaces. Uploading an export to another account does not move custom instructions, memories, GPTs, or other account settings ([transfer help](https://help.openai.com/en/articles/9106926-transfer-exported-conversations-between-chatgpt-accounts)). Keep the ZIP as a reference archive, because it is not a migration source.

## Step 3: Install the CLI and scaffold the repo

Three commands take the project from nothing to live. Install the CLI with `curl -fsSL https://kortix.com/install | bash`, scaffold with `kortix init` to create `kortix.yaml` plus the `agents/`, `skills/`, and runtime config, then run `kortix ship` to push the repo and bring it live. [Kortix on GitHub](https://github.com/kortix-ai/suna) carries the full command surface. The campaign site's [migration guide](https://chatgptworkalternative.com/migrate-from-chatgpt-work) shows the same three commands with the manifest and agent files they produce.

## Step 4: Write one agent file per set of instructions

An agent is `agents/<name>.md` for behavior plus an `agents.<name>` block in `kortix.yaml` for governance. The `.md` body is the system prompt, and it is a stock OpenCode agent file. Move each ChatGPT agent or Project's instructions into its own file, then give it a scoped reach in the manifest so it can only touch what the job needs. The scoping field is `permission`, not `tools`.

## Step 5: Move skills into the repo

Skills become `skills/<name>/SKILL.md`: markdown plus any scripts that encode how the team does one job. A skill that points at a tool also needs that connector declared, so move the two together.

## Step 6: Move memory into files

Memory becomes the `memory/` directory, plain files that accumulate as the agents work. There is no vector database to set up and no export to import. Write the facts the team wants the agents to keep, in the shape the team already uses.

## Step 7: Declare connectors

Connectors are declared in `kortix.yaml`, which sets the apps an agent may reach. Kortix reaches 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL, and raw HTTP. Connector credentials are brokered server-side and never enter the machine, so reconnect each tool once and no credential moves with the export. Each call runs under Allow, Ask, or Block, down to the arguments it was given.

## Step 8: Turn schedules into triggers

Kortix has exactly two trigger types: `cron` and `webhook`. A cron trigger fires on the clock, and a signed webhook fires on an event. Both start a session with no person present. Map each ChatGPT scheduled task to one of the two. A trigger has no "post the result to a channel" field, so the result lands in the repo the same way any other session output does, through a change request.

## Step 9: Connect your own models and keys

Kortix is model-agnostic. Point it at any model provider with your own keys, or use the ChatGPT plan you already pay for, or sign in with your OpenCode Console account for OpenCode Zen and Go. Choose the model per agent, per session, or per message. OpenAI and Anthropic models come through your own key, never as Kortix-managed models. A self-hosted instance has no managed model lineup, so every model call routes through the gateway inside the instance. The [self-hosting guide](https://chatgptworkalternative.com/self-hosting) covers the install on your own hardware.

## Step 10: Ship and verify

Run `kortix ship`, open a session, and give one agent a real task. Read the change request it opens. Start with the job that matters most, confirm the result, then add the next.

## What maps to what

| ChatGPT Work asset | Kortix file | What changes |
| --- | --- | --- |
| Custom instructions and agents | `agents/<name>.md` and a `kortix.yaml` block | Split into one file per agent |
| Plugin workflows and skills | `skills/<name>/SKILL.md` | Rewritten as markdown and scripts |
| Memory and context | `memory/` | Plain files, no database |
| Connector connections | `kortix.yaml` | Reconnect; credentials do not move |
| Scheduled tasks | `cron` and `webhook` triggers | Recreated as triggers |
| Model and provider choice | Provider keys in the project | Bring your own keys |

## What you redo by hand

Every item below is manual, because none of it travels in an OpenAI export.

- Agent instructions, rewritten as one `agents/<name>.md` file per agent.
- Skills, rewritten as `skills/<name>/SKILL.md`.
- Memory, written as files in `memory/`.
- Connector connections, reconnected and then declared in `kortix.yaml`.
- Schedules, recreated as `cron` or `webhook` triggers.
- Model provider keys, added to the project.

## What you do not carry over

Chat history stays behind as a reference archive. OpenAI's configuration schema stays with OpenAI, and the admin-console roles and assignments are replaced by Kortix account state: members, roles, and groups are live project state, not files in the repo. Secret values never appear in the repo either; `kortix.yaml` holds secret names and grants, not values.

## Questions people ask mid-move

### Can I import the ChatGPT export into Kortix?

No. The export is a copy of conversations and account data, and Kortix reads a git repo of agents, skills, memory, connectors, and triggers. Rebuild those assets as files, then commit them.

### Do my connectors and schedules move with the export?

No. The export carries neither. In Kortix you declare connectors in `kortix.yaml` and recreate schedules as triggers, one of two types: `cron` or `webhook`.

### Can I migrate one job at a time?

Yes, and it is the safer path. Write the agent file for the job that matters most, declare the connectors it needs, and ship. Each session has its own isolated sandbox and branch, so one agent's rebuild does not block the next.

### Do my API keys and models move?

The keys do not move in the export. Add your provider keys to the project, or use the ChatGPT plan you already pay for, or sign in with your OpenCode Console account. OpenAI and Anthropic models come through your own key, never as Kortix-managed models.

Read the [ChatGPT Work vs Kortix](chatgpt-work-vs-kortix.md) comparison next, or set the rules first with [Governance after migration](governance-after-migration.md).
