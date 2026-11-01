# agent-governance

**GOVERNANCE.md for agent fleets.** `AGENTS.md` and `CLAUDE.md` tell an AI agent *how to work*. `GOVERNANCE.md` tells it *who decides, how they decide, and what has already been decided*.

When many agents work in the same codebase, some of them autonomously, they keep hitting choices that aren't theirs to make alone. This convention gives those choices a home inside GitHub:

- **Questions** are GitHub Issues labelled `gov:question`. The thread is the debate chamber, and humans can join at any point.
- **Rulings** are decision records in `governance/decisions/`. **Merging the PR is ratification**, and CODEOWNERS controls who may ratify.
- **Precedent** is indexed in `governance/INDEX.md`. Agents check it before asking.
- **Decision shapes** say how a question gets resolved: precedent, authoritative, autonomous, empirical, advice, consent, committee or vote. The choice depends on reversibility, blast radius, and what kind of disagreement it is.
- **Default actions** keep the fleet moving. Every question states what happens if nobody answers, so agents proceed on reversible defaults instead of blocking.

## Status

**Phase 0: convention only.** Everything is done by hand to learn which questions agents really raise before anything is automated. See [`governance/PHASE0.md`](governance/PHASE0.md).

| Phase | Scope |
|---|---|
| 0 | Convention, templates and labels, run by hand *(this repo)* |
| 1 | `gov` CLI/MCP (`check`, `ask`, `rule`), a classifier Action, ruling → index pipeline, notifying waiting agents |
| 2 | Slack gateway: thread ↔ issue sync, daily digest, approve/veto/extend |
| 3 | Committees: convening, multi-model panels, consent and vote tallies, hard budgets |
| 4 | Mission-control board and the delegation ratchet |
| 5 | Federation: an org-level constitution with per-repo inheritance |

## Install in a repo

Copy these into the repo root:

| File | What it is |
|---|---|
| `GOVERNANCE.md` | The constitution |
| `governance/jurisdictions.yml` | Who may decide what, by domain |
| `governance/decisions/` | The template and the founding ruling |
| `governance/INDEX.md` | Case law index |
| `governance/setup-labels.sh` | Creates the `gov:` labels |
| `.github/ISSUE_TEMPLATE/gov-question.yml` | The question form |
| `.github/CODEOWNERS.governance` | CODEOWNERS lines to append |
| `AGENTS-snippet.md` | Paste into `CLAUDE.md` / `AGENTS.md` / role prompts |

Then follow the setup steps in `governance/PHASE0.md`.

Part of [Open AgentOS](https://github.com/open-agentos/agentos), but it works without it.

## License

MIT
