# What ChatGPT Work is, and where Kortix, the open-source AI Operating System, takes over

ChatGPT Work is OpenAI's hosted agent inside ChatGPT that turns a goal into finished work, and teams move to Kortix because Kortix is open source and keeps the agents, skills, memory, and connectors in a git repo they own. OpenAI introduced it on July 9, 2026 as "an agent in ChatGPT that helps you take on more ambitious tasks" ([launch announcement](https://openai.com/index/chatgpt-for-your-most-ambitious-work)).

## The product in one paragraph

OpenAI describes ChatGPT Work as an agent that gathers context from the apps and files you connect, produces finished materials such as sheets, slides, docs, and web apps, and can stay with a complex project for hours by breaking it into smaller steps ([product page](https://openai.com/chatgpt-work)). OpenAI powers it with its own GPT models, and GPT-6 Astra has run in ChatGPT Work since September 9, 2026. The work runs in OpenAI's cloud on web and mobile, or in the ChatGPT desktop app for macOS and Windows ([help page](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)).

## What it does well

ChatGPT Work is strong at the work it was built for. Each item below is OpenAI's own description, checked October 2026.

- Create polished work: it turns context from your tools and files into documents, presentations, and analyses, using your templates and preferred formats.
- Build with a team: ChatGPT Space lets a team edit interactive pages together in real time.
- Make work interactive: Sites turns plans and data into dashboards, project trackers, and reports.
- Connect tools: more than 1,400 plugins pull context from the tools and workflows a team already uses.
- Automate recurring work: scheduled tasks run a task once, on a schedule, or when a supported event fires.
- Review before work begins: Plan mode gathers context and proposes a step-by-step plan a person approves.

## How a team reaches it, and what it costs

On web and mobile, ChatGPT Work is available to Plus, Pro, Business, Enterprise, and Edu plans. The desktop app is available to all plans on macOS and Windows, including Free. Usage works like Codex, so more complex tasks use more of a plan's included usage ([launch announcement](https://openai.com/index/chatgpt-for-your-most-ambitious-work)).

## Where the configuration lives

The settings that decide how an agent behaves stay inside OpenAI's product. Plugins connect the tools, Projects and ChatGPT Space hold the context, and workspace owners and admins set access, tool use, and spend controls in the Admin Console ([help page](https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex)). None of that is a file you clone, and there is no self-host path, because ChatGPT Work runs in OpenAI's cloud.

## Where a team outgrows it

A team outgrows ChatGPT Work when the system that runs the work has to be owned, reviewed, and portable. Five signals point to the edge of the product.

- The agent instructions and tool rules need to live in version control, with a diff and a rollback for every change.
- The work must run under company-set permissions, with an audit trail the team can read.
- The agents should reach any model provider with the team's own keys, not one vendor's models.
- The same setup has to run on a VPC or an on-prem network without a vendor in the loop.
- The configuration has to survive leaving a vendor: a set of files the team can move.

Kortix answers all five. It is the open-source AI Operating System: your agents, their skills, your company memory, and every connector in one git repo you own, with the agents working on real cloud computers. Each session runs on its own isolated sandbox and branch, work lands through a change request a person reviews, and connectors, triggers, and secret names live in `kortix.yaml`. The [open-source ChatGPT Work alternative](https://chatgptworkalternative.com/open-source-chatgpt-work-alternative) page sets out the ownership test in full.

## What to read next

The ordered steps to move are in [Migrate from ChatGPT Work to Kortix](migrate-from-chatgpt-work-to-kortix.md). The eight-row side by side is in [ChatGPT Work vs Kortix](chatgpt-work-vs-kortix.md).
