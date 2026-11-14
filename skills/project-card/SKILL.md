---
name: project-card
description: Create or maintain a project's CARD.md with ranked goals, observable checks, decisions and tickets. Use for a project-card interview, running or resuming an existing card, or its end-of-run review. `/project-card light` makes the short card for a run of an evening to a few days with no money and nothing live.
license: MIT
---

# project-card

A **card** is a compact summary at `<repo>/CARD.md` that agents working that card read first. The template is [TEMPLATE.md](TEMPLATE.md); illustrative goal rows, questions and progress lines are in [EXAMPLE.md](EXAMPLE.md). Keep detail and long evidence in linked files so the card stays readable: under about 5,000 words in all, with older history moved word for word to `CARD-history.md` beside it.

The **goals** and the **done check** are the heart of the card. A goal run works toward whatever they measure, so they set how good the run can be. One goal alone gets met at the expense of everything it doesn't name.

- **Several goals.** 3–5 goals in the owner's words, each from one of four angles: **works** (the mechanism does its job end to end), **good** (an expert in the field would call the output good), **fits the owner** (their taste, time and effort), **lasts** (it keeps working, and a future agent can repeat or extend it). Every angle has a goal, or a line giving the owner's reason it doesn't matter here. Each goal carries their own "unacceptable" and "great". A side they have no words for stays `idk`, with any affected work named in Owner decides. Distinguish their direct quotes from options they selected and summaries they explicitly accepted; never attribute an interviewer's wording to them as an original quote.
- **Several levers per goal.** Each goal is pursued through two or more different levers, each its own ticket: realistic loads, varied days and a progression rule for "the training is good"; a write call and a read-back for "the routines land in the app".
- **Done is every goal.** Done means every goal's check passes. Rank decides trade-offs and where leftover time goes, never which goal may be dropped.
- **Checks are judged.** A goal's check is something the owner or the reviewer looks at and judges against their words, ideally against a reference they named. An agent's proxy metric is a ticket check until the owner adopts it as a goal check. A later check (bigger by week 12, using it for a week) names its observer, date and required evidence. Until observed, it is awaiting evidence, even if the artifact is delivered.
- **Live.** Runs update each goal's Status on the card: open, moving, passing with current evidence, slipping with why, or awaiting evidence with observer and date.
- **One output.** The done check names an output the owner can look at: a table with named rows and columns, a screen that works, a command and what it prints. Write it as a thing that will exist ("a table of these 17 portfolios with these columns from real data"), never as a question ("find whether…"). A question lets "unknown" count as done. "Insufficient evidence" may label a row of the output; it is never the output.
- **Locked.** Goal wording, rank, goal checks and the Done check change only on the owner's explicit instruction or acceptance. Runs update the Status column, tickets, open decisions and evidence. Agent-written tests go under tickets; they do not replace approved goal checks.
- **Tight anchor.** The title, Goals section and Done check are the card's anchor. A lead card run keeps them in front of the lead (read it at session start and after every compaction), and its reviewer grades each milestone against every clause in them.
  - Keep each goal check to the observable result, the owner's own numbers and reference, and the few rules that must hold exactly, about 100 words.
  - Keep the Done check to its four template lines, about 250 words. When the output has rows, columns or parts, list them under the Output line, one per line, never in a paragraph: the lead rereads the anchor after every compaction, and an item on its own line survives that reread where one buried in prose does not.
  - Keep the whole anchor under about 1,500 words in the draft.
  - The owner's quotes and selected options stay word for word and take precedence over these budgets; trimming comes from agent-written text.
  - Agent-set thresholds and file names go in ticket checks. Planted errors, test steps and procedures go in a design file linked under Limits (Detail lives in); the ticket check names the file and section, and the lead reads it when it works that ticket.
  - Keep each Status cell to its legend entry and an evidence link; the evidence itself goes in the progress log or Run log.
- **Proved.** Project done requires the actual done-check output, every goal passing, and no unresolved blocking review finding. The Run log holds concise results and links to longer evidence. A completed review report can still describe a paused or failed project.

A card records intent and existing authorization; it grants no extra permission to access accounts, spend, delete, publish, change harness settings or launch another runtime. Honor the request's scope and repository rules. Making or reviewing a card does not start its implementation.

Find the branch that matches the request and follow it.

## Which card

- **Full card** (Make a card): money, trading, accounts, anything live, or a run longer than about a week.
- **Light card** (Make a light card): a run of an evening to a few days with no money and nothing live, where the worst case is a wasted evening. The owner asks for it with `light` in the request; without that word, make a full card.
- **No card:** an afternoon's task the owner would check themselves within the hour. Use a plain prompt that says what done looks like, and ask the owner directly when a decision is needed.

## Make a card

1. Read the existing card and relevant README, briefs, plans, repository instructions, recent history and already-authorized data. Preserve existing goals and unrelated work. A pasted prompt or agent-written brief is source material unless the owner explicitly adopts it as their requirements.
2. Use the interview below to resolve only missing owner decisions. Reuse their explicit answers and accepted requirements; do not repeat an interview whose answers are already available.
3. Draft the card from [TEMPLATE.md](TEMPLATE.md):
   - Goals: the headline sentence and ranked table, each with its source question or accepted requirement, unacceptable/great and Status `open`. Mark selected options and accepted summaries as such.
   - Done check: the output at the size the owner asked for (all 17 portfolios, all 12 weeks); the command an agent runs to produce it; the first thing the owner does to use it. Their first-look slice is what the early tickets build and show them, not a smaller done. The first look is shown, not waited on: its ticket's check is the output existing on real inputs, never "the owner says whether…"; the run shows it and goes on to the next milestone, and their reaction redirects the run when it comes. Only their own last step waits for them. The output's rows, columns and parts go as indented lists under the Output line, one item per line (TEMPLATE.md shows the form), so a reread can't lose one.
   - Facts from the owner: every number and preference from the interview that the output depends on.
   - Ambition: propose a big version, the most ambitious one that still has a done check. The owner keeps or cuts it.
   - Tickets: 5–15, ordered, each one outcome with its own check and the numbers of every goal it moves. Every goal has at least two tickets pulling different levers. Plumbing gets as few tickets as it needs to work once. The last ticket is the owner's own step (play it, build it, use it for a week), with a date. If the owner won't do that step, say so before anything gets built.
   - Assumptions: every assumption the output rests on (units, what exists, what the owner can lift) is a Fact from the owner or an early ticket that tests it. Forming a hypothesis isn't the failure; treating it as true without a test is.
   - Checks: each ticket's check looks at the effect in the output or the world, never only that a command ran.
   - Ticket 1: when the project rests on something that might not work, a bounded test that could say no, within the agreed budget. If it says no, record the evidence and pause the dependent work; the original goal remains unmet. Otherwise, build the first-look slice end to end.
   - Targets: when the math says a goal is implausible (a return, a timeline, a money amount), put the math in Owner decides before building.
   - Run may decide / Ask the owner first: the decision boundary from the interview. A long run without one either stalls on small calls or makes big ones it shouldn't.
   - Owner decides: owner questions and every remaining interview gap under 0.8, with its score and affected tickets. An unresolved authorization or acceptance boundary blocks dependent work; if its effects cannot be bounded, it blocks execution.
   - One card per goal set: when a new tool, harness or model comes along, it continues this card and repo.

   Preserve their own words and explicit selections. Proposals remain labeled proposals until accepted; existing explicit acceptance counts and needs no repeated confirmation.
4. Measure the draft's anchor (`awk '/^## /{keep = /^## (Goals|Done check) *$/} keep || NR==1' <draft file> | wc -w`) and the whole card (`wc -w <draft file>`, under about 5,000 words) and trim agent-written wording to the tight-anchor sizes; accepted goal checks and the Done check shrink only with the owner's acceptance. Then show the draft once and apply their answers. Any clarification or draft-review questions use the same tool/fallback and count toward the same 12-call limit. A "you decide" delegates that item within existing limits. At the limit or when they stop, save unresolved items and leave the card a draft wherever the kickoff gate is unmet; do not start another question loop.
5. Write `CARD.md` at the repo root, preserving any existing card. Keep the interview record as described below. Add the following pointer once to the repo's startup instructions (`AGENTS.md`, or its established equivalent), preserving existing content: `For card work, read CARD.md first and follow the project-card skill. Questions for the owner go in its Owner decides list.` If another run is editing that checkout, stage the draft and its record outside the checkout at explicit paths and report them; do not replace its active card or launch a run from the staged draft.

Card creation ends with a compact card and its remaining decisions recorded. Mark it ready only when the kickoff gate passes; otherwise mark it draft with the affected work blocked. Keep one line per ticket and link detail.

### The interview

**Ask with a question tool usable in the current mode.** Use an available native question tool with a working renderer. Otherwise ask one plain-chat question and wait. Use the same fallback for draft review; starting another runtime just to ask requires separate authorization.

Ask one judgment per call; up to three independent facts may share a call within the tool's schema limits. Wait for the actual submitted answer before dependent work. An asynchronous tool returning, an elapsed timer or a preselected choice is not an answer. Look up already-authorized, findable facts first, and ask only what only the owner knows. When a found fact needs confirmation, show its source.

**Record as you go.** After each answer, append its question ID, exact question and offered options, submitted selection and free text to the interview record. Preserve wording except explicitly marked redactions. `CARD-interview.md` may hold the non-sensitive record; keep credentials out of it and omit unnecessary personal/account identifiers. Keep needed sensitive detail in an authorized private location outside version control, with a redacted reference on the card. Do not reconstruct a missing answer after compaction or overwrite an earlier record. This is a record of the card interview, not a copy of the whole session.

**The question's shape follows what it asks.**
- Goals are judgments. Prefer their own examples; offer 2–3 contrasting prompts only when useful. Quote submitted free text as their words. A label-only answer is recorded as `selected option: <label> (Q#)`, not an original quote; a proposed summary needs their acceptance before it is locked. An unanswered unacceptable/great stays `idk`. After a multi-pick, ask which wins a trade-off; retain all selected requirements unless they explicitly drop one.
- Facts and either/or decisions: 2–4 answers that exclude each other.
- The output: show it before asking about it. Give each option a preview (an ASCII screen, three sample rows, the first lines of the plan) and ask which is closest and what's wrong with it.

Use five clarity scores from 0 to 1 to choose the next useful question: `Clarity: output 0.9 · goals 0.4 · facts 0.2 · first look 1.0 · limits 0.7 → asking: facts`. These are interview heuristics, not measured probabilities or authorization. Anchors: 0 means no usable answer, 0.5 means enough for a bounded first step, and 1 means the stated criterion below is explicit. Start with goals move 1 unless already answered, then address the lowest score. Digging into a conclusion, resolving a trade-off and the pressure pass may take priority, within the same call limit.

| Gap | Scores 1 when |
|---|---|
| Output | they have reacted to a sketch of the exact thing they'll look at; a named output they haven't seen scores at most 0.6 |
| Goals | 3–5 goals with checks in their words, each with their unacceptable and great, every angle covered or waived with their reason, ranked |
| Facts | every number, account or preference the output depends on (current lifts, budget, which account, the equipment) has their value |
| First look | they have named the slice they check before anything scales (week 1 before week 12, one page before the site) |
| Limits | non-goals, money, risk, what must stay exactly as it is (their existing data, their phone's sign-in), and the decision boundary: what the run may decide alone and what it asks them first |

Goals come from three moves:
1. Ask "When you first open it, what would make you say 'unacceptable'? And what would make it great?" Sort their answer onto the four angles. Each concern becomes a goal with its check, and their phrases become its unacceptable/great.
2. For empty angles, ask once per angle: "Anything on <angle>, or doesn't it matter here?" Independent angles may share a call within the tool's question limit. Record only the owner's actual waivers.
3. Ask once: "When these pull against each other, which wins?" That gives the rank.

When an answer is a conclusion ("too light", "it sucks"), ask for the number or example behind it before treating it as an acceptance check.

**Pressure pass.** Before drafting, go back to at least one earlier answer, the rank-1 goal's first, and push it one rung, with the options left open ("I'll name one" · "none comes to mind") so the answer is theirs: the example ("which app already feels right?"), the assumption under it ("what makes the current one feel wrong?") or the boundary ("what would you cut to get it?"). A goal check that names their reference can be judged; "good" alone can't.

A missing fact is a question now. A timid default later (conservative estimates, placeholder copy, the same item repeated to stay safe) fails the **good** goal.

Around the fourth call, ask once: "What's the simplest version you'd still use?"

Stop when every score reaches 0.8 and the pressure pass is done, after 12 question calls total including draft review, or when the owner says stop. Batch facts count as one call. Only the owner may extend the interview budget. Save unanswered items, their scores and affected tickets; exhaustion never supplies an answer, waiver or permission.

## Make a light card

The same card, same template, every section heading kept, with short sections and a four-call interview. Put `· light` at the end of the status line, so the kickoff gate and the reviewer judge it by the light gate below.

The interview, at most 4 question calls under the same tool rules and record, stopping early when the owner says "you decide" for the rest:
1. "When you first open it, what would make you say 'unacceptable', and what would make it great?" In the same call, which of the four angles don't matter here; their words go under Not goals. No pressure pass.
2. The output, shown as a sketch before they are asked about it, and the first look they check before anything scales. Ask here: "What's the simplest version you'd still use?"
3. One batch: the facts the output depends on, money and risk, what must stay as it is, and the decision boundary (what the run decides alone, what it asks them first).
4. The draft, once.

The card: 1 to 3 goals (works always; the others they named), each check about 50 words in their words, `idk` where they gave no unacceptable or great; the Done check's four lines; Facts from the owner; Ambition with the first look (shown, not waited on) and `Big version: none` unless they gave one; Owner decides; 3 to 6 tickets, each with a check and its goals, the last one their own step with a date; Limits with Run may decide, Ask the owner first, Must stay as it is, and Budget and stop; an empty Run log. Keep the whole card under about 1,000 words.

**Light gate.** The card is ready when the Done check names an output they will look at, the first look is named, Run may decide and Ask the owner first are written, every ticket has a check and names a goal, and each waived angle carries their words. Three goals, two levers per goal and unacceptable/great on every goal are not required. If money or something live turns up mid-run, the run stops with that as its question and the owner runs the full interview on the same card; its answers are reused.

## Run a goal from a card

**Kickoff gate.** A card whose status line ends `· light` is checked against the light gate in Make a light card instead of this one. Check the card before handing over or starting execution: 3–5 ranked goals with accepted checks, unacceptable/great evidence (or explicit `idk`) and Status; every angle covered or waived by the owner; every ticket names its goals; each goal has two tickets using different levers. Required scope, acceptance and decision authority must be explicit for the work to start. Map every unresolved item to affected tickets; unknown impact blocks execution. An `idk` may remain only where the accepted check is still usable. On failure, record the blocker and leave dependent work paused; further interviewing requires remaining question budget or the owner's extension. Already-authorized, independent investigation may continue within its stated limits.

The kickoff references the card, not a rewritten goal. When the owner asks for a kickoff, give a prompt for their current agent, run from the repository root:

```text
Work the card in ./CARD.md. Follow its approved Goals, Done check and Limits. Finish and check each eligible milestone, then continue to the next authorized milestone. Stop with the exact blocker and resume condition when the remaining work requires an owner decision, a later observation, more budget or new authorization.
```

Giving a prompt launches nothing. Use the owner's current, authorized agent and review tools. This skill installs no profile, hook, goal loop or runtime protection for locked sections. Read the card's title, Goals and Done check at startup and after compaction, and preserve their approved wording. A requested launcher command must come from the installed tool's current help; no particular CLI, provider seat or local wrapper is required.

In a lead card run, work goes in milestones. Milestone 1 is the first-look path running end to end on real inputs; each later milestone is the next slice the lead can finish and check. A milestone ends **done** (built, checked, reviewed and re-checked; continue to the next eligible authorized milestone) or **waiting** (the milestone can't go further without the owner, a later date or a worker cap in Limits, and the stop opens with the one question or wait). The first look is shown, not waited on. Project done stays the Done check plus Owner's verdict: their own final step and their verdict stay theirs, and the Run log's verdict column stays blank for them.

- Milestone 1 is the first-look path running end to end on real inputs; work elsewhere before it runs counts as drift unless the first look is blocked (name the blocker). Then spend time on the goals in rank order, the hardest eligible part of the top goal first. Use the Effort line to avoid unnecessary tooling and repeated checks; it does not waive repository checks or safety requirements. Repeat relevant validation after a change that could invalidate earlier evidence.
- Judgment outputs (a training plan, a design, a recommendation, copy) get built the way a skilled practitioner would ship them, and checked against each goal before the end-of-run review.
- Make decisions within Run may decide and existing authorization. Record new questions on Ask the owner first with affected tickets; reuse any explicit authorization the owner has already given. A blank or unresolved boundary grants no authority.
- When a check fails or the owner reports a problem, establish the facts and the cause first (is it so, how much, why), then act. A suspected cause stays a hypothesis until a check confirms it, and only a confirmed one becomes a lesson in `AGENTS.md`. When the owner rejects an output, re-read the goals and rethink the approach; the complaints they named are symptoms, and patching them one by one leaves the cause in place.
- A ticket is done when it moves its goals and leaves the others whole. Before closing one, look at what it did to every other goal; a change that sets one back reopens the ticket.
- **Keep the goals in view.** `CARD.md` is authoritative for approved goals, limits and current Status. When a ticket closes, update its Status and the goals' Status cells. When a milestone finishes, append one dated Run log line covering every goal (`G1 moved: …; G2 unchanged; G3 slipped: …`) with its check's actual output, about 40 words with a link to the evidence. Ticket Status cells stay a few words plus a link; answered Owner decides items shrink to one line with the owner's words and the date. When the card nears about 5,000 words, move the oldest Run log rows and answered items, word for word, to `CARD-history.md`. Only that history moves: the owner's accepted text (Goals, Done check, tickets' outcomes and checks, facts, limits, open decisions) stays even when it alone passes the budget; a card that needs trimming there is the owner's call. Historical rows stay historical; avoid a second mutable goals table. Card runs keep no separate plan or progress files.
- After compaction or restart, read the whole card (Status, Owner decides, the last Run log rows), `git log` and this session's review reports before continuing; ignore any `.planning` folder unless the owner names it. Resolve stale status against current evidence; do not overwrite approved wording. Installing a compaction hook is a separate, explicitly requested configuration task, not part of a card run.
- The project is **done** only when the done check and all goals pass with current evidence and review has no blocking finding, and that verdict is the owner's. A run stops at a milestone: **done**, or **waiting** when the milestone's remaining work awaits an owner answer or dated observation, budget is exhausted (including any worker cap set in Limits), a feasibility test fails, or no safe authorized next step remains. Tickets outside the milestone don't have to be exhausted before waiting. The stop message opens with the one question or wait in plain words: the blocked ticket, why only the owner or a date unblocks it, what each answer leads to and the lead's pick. A question asked through a question tool stays first in every stop message until the owner answers. Record completed output, failed or pending checks, affected tickets and the exact resume condition. All tickets closed with a failed goal is not done; find an in-scope repair within budget or wait. A future outcome stays awaiting evidence until its observer supplies it.
- A question for the owner goes into Owner decides with the ticket it blocks. If it blocks the current milestone, the run may stop and wait on it; otherwise the run moves on to the next ticket it can do. A question that blocks nothing in the milestone never justifies stopping.
- The owner's mid-run ideas: build one when it moves a card goal within the card's limits and budget; otherwise answer it in words and, if it's a real option, record it under Owner decides. An idea never changes Goals or the Done check. Extensions past the Done check (more weeks, more pages, more features) go to the card's Big version or a new card, and work on them starts only after the owner fills in their verdict.
- One ticket at a time. Tickets that own separate files may run in parallel, each in its own worktree.
- Update ticket Status as it changes. Card runs don't use plan-files: the card, git and the review reports are the working state.
- Runtime lines in older cards must be checked against the owner's current, authorized tools. A card's review before going live is that milestone's review plus one re-check, and its end-of-run review stays the project's. Installing or changing a runtime requires separate authorization.
- When the owner corrects something and the cause is confirmed, record a concise lesson in the repository's established agent instructions when that edit is authorized. If the correction repeats, propose a check that catches the mistake; implement it only within the task's scope.

## End-of-run review

1. Record the exact reviewed commit or file state. Run safe, repeatable checks on current files and record actual results for the done check, goals and tickets. For a check that writes a live account, spends, deletes or otherwise repeats a consequential action, inspect its existing execution receipt and current read-back instead; exercise changes in an authorized fixture or sandbox. Never replay a live mutation just to collect review evidence.
2. A fresh reviewer from the other model family reads the card, available non-sensitive interview record, diff and results. Use already-authorized, available tools and current routing rather than pinned model versions. Source and product data remain read-only; safe tests may use isolated scratch outputs. If cross-family review is unavailable, record the review gap and leave completion paused; same-family advice does not satisfy this gate.
   - Review each finished milestone, fix confirmed findings, then have the same reviewer re-check the changed lines and open findings once. There is no third round. If a required reviewer is unavailable, keep the affected completion or release paused and state the gap. The end-of-run review judges the whole project once the Done check's observations are available.
   - Money, accounting, trading, auth, secrets, deletion, shared configuration, or more than about 400 changed lines require independent review of correctness and design failure modes before merge or release. Apply the repository's stronger process when one exists.
3. Compare actual output against the approved Done check at the full requested size. Independently verify the user's command and first-use behavior through safe checks, current read-back or an authorized sandbox; label any unexercised live path. Judge every goal against the owner's wording, selections and unacceptable/great. A missing or failing required goal gets REQUEST CHANGES, whatever its rank; a dated check with no observation remains awaiting evidence. Passing agent-written tests alone cannot establish acceptance.
4. The lead fixes the findings it confirms and answers the rest with evidence.
5. The same reviewer re-checks once: changed lines and open findings only. Keep unresolved blocking findings blocked and list any owner decision in Owner decides; recording one does not close it or waive it.
6. Append a concise Run log row: date, reviewed revision, tickets done, actual output or its evidence link, each goal's pass/fail/awaiting result and why, review verdict and one lesson. Mark the project done only under the done rule above; otherwise paused with reason and resume condition. Leave Owner's verdict blank for them: kept, fixed or redone. Keep long output and sensitive details out of the summary.

The review is recorded when its evidence, goal results and findings are in the log. The project is done only when every approved check passes, required review is satisfied and no blocking finding remains. Pending observations, missing review and documented failures remain visible as paused work.
