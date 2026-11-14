# Agent workflow skills

Two skills for agents that read the Agent Skills `SKILL.md` format.

| Skill | Use it for |
|---|---|
| [project-card](skills/project-card/SKILL.md) | Interview the project owner, write one `CARD.md` with approved goals and a visible done check, then keep decisions, tickets and results current across runs. |
| [ds-review](skills/ds-review/SKILL.md) | Review a completed data analysis and its number-producing code before sharing it. Block release when consequential claims lack evidence. |

## Copy a skill

Copy the whole `skills/project-card` or `skills/ds-review` directory, including its `LICENSE`, into the skills folder your agent reads. Keep its template, example, prompt and reference files beside `SKILL.md`. Each folder includes the original MIT copyright and permission notice. Retain that notice when copying or redistributing the skill. You can copy either skill independently.

Ask your agent to use `project-card` to make a card, use `project-card light` for a short project, or use `ds-review` to review a completed analysis. Creating a card does not start the project. A review does not authorize publication or access to new data.

## What you need

`project-card` needs local file access. Running a card needs the owner's authorization and an independent reviewer from another model family. If that reviewer is unavailable, the skill records the gap and leaves completion paused. The owner supplies any agent launcher and any stronger repository review process. This copy includes no custom profiles, hooks, automatic goal loop or enforcement of locked text.

`ds-review` needs the completed report, its number-producing code or queries, data provenance and reproduction evidence, plus a fresh read-only reviewer context. The driver runs trusted checks on authorized local data. The reviewer reads the packet. It does not execute code or receive unauthorized raw data. A different model family is preferred for this skill, but is not required.

These are portable copies of the author's workflows. The project-card copy uses "the owner" instead of a personal name and replaces machine-specific launchers and unshipped helper skills with explicit startup and review instructions. The data-analysis review instructions are unchanged. Its compatibility note lives here so both skill files use frontmatter accepted by Codex's skill validator. The examples are fictional.

## License

MIT. See [LICENSE](LICENSE).
