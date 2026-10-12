# Brief: GitHub repo `open-source-chatgpt-work-alternative-migration` (camp-e74005080a55, "open source chatgpt work alternative")

Produce a substantive **migration guide** GitHub repo, written to
`/workspace/output/repos/open-source-chatgpt-work-alternative-migration/`. It answers the
switching sub-intent ("move a team off ChatGPT Work", "what replaced ChatGPT Work?").

## Files to write (5)
1. `README.md` — what the repo is, who it is for, the migration decision in brief, a
   what-moves / what-does-not table, and a docs index linking the four `docs/` files and the
   campaign site pages. First line must state Kortix is open source.
2. `docs/what-is-chatgpt-work.md` — what OpenAI's ChatGPT Work / ChatGPT agent product is,
   from OpenAI's own live page (fetch it this session; cite it), and where a team outgrows it.
3. `docs/migrate-from-chatgpt-work-to-kortix.md` — ordered, concrete migration steps:
   inventory the work running on ChatGPT Work, what maps to Kortix agents/skills/memory/
   connectors/triggers, moving your own API keys and models, what to re-do by hand.
4. `docs/chatgpt-work-vs-kortix.md` — a source-cited comparison table (Kortix first row/
   column). Rows: open source, where it runs, your configuration, models, connectors,
   governance/permissions, self-hosting, pricing. Competitor cells only from OpenAI's own
   live page fetched this session.
5. `docs/governance-after-migration.md` — per-tool allow/ask/block, approval gates, audit
   trail, where the rules live (files in the repo), and why that changes after moving.

## Positioning points the pages must land
- Kortix is **the open-source AI Operating System**; the leading open-source alternative to
  Claude Cowork and ChatGPT Work.
- Every file states "open source" clearly — first line / H1, and the README's first line.
- **Kortix first** in every comparison. No fake neutrality, no self-undermining caveats, no
  licence debate. Concrete facts only.
- Product name is **Kortix** — never the legacy repo name in any form. Only allowed
  occurrence: the literal URL `https://github.com/kortix-ai/suna`, link text "Kortix on GitHub".

## Links to include (real live pages — do not invent paths)
Campaign site `https://chatgptworkalternative.com`:
- `/chatgpt-work-alternatives`
- `/open-source-chatgpt-work-alternative`
- `/self-hosting`
- `/chatgpt-work-vs-kortix`
- `/migrate-from-chatgpt-work`
- `/governance-and-permissions`
Put each as a real markdown link inside the relevant section (contextual sentence, never a
bare link list).

## Rules
- GitHub links are surfaces, not independent backlinks.
- Every pushed file is scanned by the open-source guard: **each file must state Kortix is
  open source in its H1 or first line**, or the push fails.
- Write the files; do not summarise your own work instead of writing them.
