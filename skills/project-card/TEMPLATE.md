# <Project> card

Updated <YYYY-MM-DD> · Status: draft | ready | active | paused (<reason; resume condition>) | done [· light, for a card made by the skill's light branch: same sections, short, judged by its light gate]

## Goals

Accepted goals, locked: wording, rank, checks and the Done check change only on the owner's explicit instruction or acceptance. Runs update only the Status column here. Rank settles trade-offs; done requires every goal's check to pass and no blocking review finding.

<One sentence: what is true for the owner when this is done.>

| Rank | Goal (owner quote, selected option or accepted summary; source) | Unacceptable / great (source, or idk) | Angle | Check (what is observed, by whom and when) | Status |
|---|---|---|---|---|---|
| 1 | <goal; Q# or accepted requirement> | <their answer or selected option> / <their answer or idk> | works / good / fits the owner / lasts | <what is judged against their reference, about 100 words at most; observer and date for a later check> | open |

Status: open · moving (ticket #) · passing (current evidence) · slipping (why) · awaiting evidence (observer, date). CARD.md is authoritative; progress entries are historical snapshots.

Not goals: <angle>: <the owner's reason it doesn't matter here> (only for a waived angle)

## Done check

- Output: <the thing that will exist when this is done, at the size the owner asked for: a table, a screen that works, a file with this content>. Its rows, columns and parts one per line, never in a paragraph:
  - Rows: <one per line: each alternative, case or record the output must hold>
  - Columns: <one per line, with units and what each is measured against>
  - Parts: <one per line, when the output has more than one piece: the table, the map under it, the header>
  - <any other list the output is made of, one item per line>
- Every goal's check passes with current evidence and required review has no blocking finding. Awaiting evidence is not a pass.
- Agent check: `<command>` → <that output; classify as safe to repeat or a mutation requiring an existing receipt and read-back>
- Owner uses it: <the command they type or the first click, and what they should see>

## Facts from the owner

Interview evidence: <link to non-sensitive CARD-interview.md, or an authorized private record; preserve wording except marked redactions; no credentials or unnecessary personal/account identifiers>

- <fact the output depends on>: <their value, in their words> · <YYYY-MM-DD>

## Ambition

- First look: <milestone 1: the early slice the owner checks before scaling, run end to end on real inputs before other work; the Done check still covers the full requested output>
- Big version: <the most ambitious version that still has a done check>
- Not now: <deliberately left out>

## Owner decides

Agents record unanswered owner decisions here and continue only authorized, independent tickets. Unbounded authorization or acceptance gaps block execution. Answered items shrink to one line: the question, the owner's words, the date.

- [ ] <question; clarity score if an interview gap> (blocks: ticket <#s> | all execution | nothing, with reason) · asked <YYYY-MM-DD>

## Tickets

| # | Goals moved | Outcome (one lever) | Check | Status |
|---|---|---|---|---|
| 1 | <goal #s, e.g. 1, 3> | <one outcome> | `<command>` or <observable result> | todo |

Ticket status: todo · moving · done (evidence) · blocked (decision) · awaiting (observer, date), plus a few words and an evidence link. Reopen a ticket that regresses another goal.

## Limits

- Effort: the goals get the time, in rank order. Verify the done check, goal checks and real use through safe paths, with integration tests where a break matters. Each milestone: one review before anything goes live, one re-check of the fixes; one end-of-run review when the Done check's observations are in. Repository and safety checks still apply; skip tests that only restate implementation and repeated checks unsupported by a change or failure.
- Run may decide: <calls the run makes alone, from the interview: libraries, layout details, which of two tools>
- Ask the owner first unless already explicitly authorized: money, live trading, deleting data, merges to main, <from the interview>. The card grants no additional authority.
- Must stay as it is: <their existing data, settings or habits the run leaves untouched>
- Budget and stop: <time, spend or quota; pause when exhausted and record output, blockers and resume condition>
- Detail lives in: <links to the design, spec, decisions and long evidence>

## Run log

| Date · revision | Tickets done | Actual output / evidence link | Goals (pass/fail/awaiting, why) | Review · next action or lesson | Owner's verdict |
|---|---|---|---|---|---|

One row per finished milestone, about 40 words with a link; when the card nears about 5,000 words, the oldest rows move word for word to `CARD-history.md`. Recording a review does not mark the project done. A paused run names its reason and exact resume condition; the owner fills in their own verdict.
