# Governance after migration: how Kortix, the open-source AI Operating System, controls agent work

Moving agent work from ChatGPT Work changes who can change the rules. The per-tool policies, approval gates, and grants stop being admin-console settings inside a vendor's product and become files in a repo the team reviews, and Kortix is open source. The move ends in a checklist, and it follows below.

## What governance looks like on each side

In ChatGPT Work, workspace owners and admins control the people and the product surfaces their role can reach: access to connectors and tools, network access for cloud environments, and spend controls, all in the Admin Console, with oversight through the Compliance API ([workspace agents](https://openai.com/index/introducing-workspace-agents-in-chatgpt), [help page](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)). In Kortix, the same decisions are split between repo files and account state, so a rule is either a file you can diff or a live setting you can see.

## Where the rules live

| Rule | Where it lives | Repo file or account state |
| --- | --- | --- |
| Agent behavior | `agents/<name>.md` | Repo file |
| Agent reach and grants | `agents.<name>` block in `kortix.yaml` | Repo file |
| Connector and per-call policy | `kortix.yaml` | Repo file |
| Triggers | `kortix.yaml` | Repo file |
| Secret names and grants | `kortix.yaml` | Repo file |
| Members, roles, groups, audit | The account | Live state |

`kortix.yaml` declares the machine image, the connectors and triggers, and the secret names and grants. Secret values never appear in the repo. There is no Members node in the manifest: members and roles are live project state, not a file.

## Per-tool policy: allow, ask, block

Every connector call runs under one of three policies, shown in the interface as Allow, Ask, or Block. The code names are `always_run`, `require_approval`, and `block`. An Ask holds the call, and the agent's turn pauses and resumes when a person decides. Give an agent a job and set each tool to Allow, Ask, or Block, down to the arguments of each call.

Approval gates you set, and they are off until you set them. Until a rule is set, a connector call runs without a pause. The default comes from the manifest, where the policy key nests like this:

```yaml
policy:
  default_mode: allow_all
```

Change `default_mode` or set a per-call rule to move a step from running to waiting.

## The approval gate and the change request

Session work reaches `main` through a change request, and merge is default-deny for agents. A session can never merge a change request it opened itself, whatever it has been granted. Opening and merging are separate permissions, `project.gitops.push` and `project.gitops.merge`, so a token can open change requests without the power to merge them. Nothing merges itself: work reaches `main` through a change request a person approves, unless an admin granted the merge capability. An agent can edit its own configuration on its session branch and propose the change, and a person approves it.

## The audit trail

Every action is recorded. Reading, exporting and streaming the audit log depend on the plan. Roles, groups, and an audit trail cover people and agents, so the same record answers who did what and which agent proposed it.

## Identity and secrets

SAML 2.0 single sign-on and SCIM 2.0 cover the people side. Per-resource permissions cover people and agents. Secrets are encrypted at rest with a key per project, and connector credentials are brokered server-side and never enter the machine. A secret has an exposure, and environment is the default exposure; egress-enforced is experimental.

## Why this changes after the move

The rules become repository state. A change to an agent's reach, its tools, or a trigger arrives as a diff you review, and the same access model travels with the repo wherever it runs. An agent carries two bindings: the role bound to its service account and the Kortix permissions its manifest declares. A session can only do what both allow, and the two bindings never widen each other. On the hosted side, the same decisions lived in a console you reach through a login.

## The governance checklist

Set these before the first agent runs.

- [ ] Decide the default mode. Leave it `allow_all`, or set the baseline the team wants.
- [ ] Set Allow, Ask, or Block on each connector call, down to the arguments.
- [ ] Turn on approval gates for the steps that matter. They start off.
- [ ] Scope each agent's reach in its `agents.<name>` block.
- [ ] Keep merge default-deny, and keep `project.gitops.push` and `project.gitops.merge` separate.
- [ ] Review every change request before it lands on `main`.
- [ ] Decide the audit access the plan allows, and who can read, export, or stream it.
- [ ] Connect SAML 2.0 and SCIM 2.0 if the team is on an identity provider.
- [ ] Keep secret values out of the repo and grant them per project.

The campaign site covers the same ground on its [governance and permissions](https://chatgptworkalternative.com/governance-and-permissions) page. The move itself is in [Migrate from ChatGPT Work to Kortix](migrate-from-chatgpt-work-to-kortix.md).
