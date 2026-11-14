---
name: ds-review
description: Review completed data analyses before sharing. Use to red-team, audit, validate, or approve a finished report and its number-producing code or queries for statistical, logical, reproducibility, data-integrity, or privacy defects. Optionally write an evidence-locked executive summary after PASS. Skip unfinished exploration, analysis creation, chart or deck generation, and external posting.
license: MIT
---

# Data Science Review

## Purpose

Gate a completed analysis before it is shared. Independently review the report and every artifact that produces a reported number, require the driver to reproduce each blocker against real data, and release only after a fresh review returns `PASS`.

This skill reviews an analysis; it does not replace the analyst, run an open-ended exploration, create charts or decks, or post results anywhere.

## Activation

Activate when a completed analysis is being red-teamed, audited, validated, approved, or prepared for release. Activate even when its review packet is incomplete; a material omission is a blocker.

Do not activate for:

- unfinished exploratory analysis;
- requests to perform a new analysis;
- chart, dashboard, or presentation generation;
- copyediting without analytical review;
- posting to Slack or another external system.

## Roles and invariants

- **Driver**: assembles the packet, runs existing code and approved checks against real data, triages findings, fixes the analysis, reruns the full number-producing path, and controls release.
- **Reviewer**: works in a fresh, separate, read-only context. Prefer a different model family when one is available, but never require a provider or model selector.
- The reviewer inspects only authorized packet contents. It does not mutate artifacts or execute code.
- The driver never executes reviewer-authored code. The reviewer specifies a discriminating check; the driver implements or runs the smallest trusted local check.
- Raw row-level data stays local and is included only when authorized and necessary. Prefer schemas, data dictionaries, snapshot metadata, staged row counts, and reproducible queries.
- While verdict is `BLOCK`, keep the report and any summary local. Never share first and repair later.

## Workflow

### 1. Classify the analysis

Choose one primary shape and every materially applicable secondary shape:

- descriptive or usage;
- churn or retention;
- funnel;
- controlled experiment;
- observational or causal;
- cost, pricing, or margin.

Record the classification and why it applies. Descriptive or usage work uses the universal checklist only. For other work, use the universal checklist plus each matching conditional section in [`references/review-checklist.md`](references/review-checklist.md). Do not load unrelated conditional sections.

**Complete when:** every consequential claim is covered by the universal checklist and each applicable analysis shape.

### 2. Assemble the review packet

Include:

- the decision or question being answered;
- the complete report;
- every script, notebook, transformation, or query that produces a reported number;
- exact run commands, required environment, parameters, and seeds where applicable;
- source provenance, snapshot identifiers, freshness dates, schemas, and data dictionaries;
- metric definitions, unit of analysis, population, eligibility rules, and time window;
- row counts after every material filter, aggregation, and join, including unmatched counts and key cardinality where relevant;
- the reconciliation target and observed result;
- known caveats, assumptions, planned-versus-post-hoc status, and prior corrections;
- the allowed data boundary and any privacy or disclosure constraints.

For warehouse-only work, provide reproducible query commands, snapshot dates, query parameters, schemas, and staged reconciliation counts instead of copied row-level data.

Do not substitute prose for the number-producing path. If an artifact needed to support a consequential claim is unavailable, state that gap in the packet rather than guessing.

**Complete when:** a reviewer can trace every consequential claim to its code or query, inputs, parameters, and reconciled output without requesting unauthorized data.

### 3. Run an independent read-only review

Start a fresh reviewer context and provide:

1. the review packet;
2. [`assets/review-prompt.md`](assets/review-prompt.md);
3. the universal checklist section;
4. only the conditional checklist sections selected in step 1.

The reviewer traces each consequential claim to the number-producing path and packet evidence. A missing material artifact is evaluated as missing evidence, not silently waived.

**Complete when:** the reviewer has returned the strict verdict schema below and accounted for every consequential claim.

### 4. Return a strict verdict

The first line must be exactly one of:

```text
VERDICT: PASS
VERDICT: BLOCK
```

Then return:

```text
## Findings
| ID | Severity | Report/code location | Affected claim | Concrete evidence | Why it fails | Discriminating check | Minimal fix |
|---|---|---|---|---|---|---|---|

## Coverage
- Analysis shape(s):
- Consequential claims checked:
- Artifacts not reviewed:
- Checklist sections applied:
```

Use only these severities:

- **BLOCKER**: a claim or recommendation may be wrong or unsupported; a key result cannot be reproduced; a material uncertainty is concealed; or sensitive data could be disclosed.
- **NIT**: the analysis is safe to share but imprecise, unclear, or weakly documented in a way that cannot materially change a claim or disclose sensitive data.

`PASS` requires zero blockers. `BLOCK` requires at least one blocker. List every blocker; never hide blockers behind a finding cap. Limit NITs to the 15 highest-value items. Treat a materially unresolved uncertainty as a blocker.

**Complete when:** verdict, severity, and finding count obey these rules and every finding contains concrete packet evidence plus a discriminating check.

### 5. Triage, repair, and re-review

For every blocker, the driver must:

1. reproduce it against the real local data using the existing analysis path or a minimal trusted check;
2. mark it `accepted`, `rejected with evidence`, or `unresolved`;
3. fix every accepted finding at the number-producing source and update affected prose;
4. preserve evidence for rejected findings in the packet;
5. rerun the entire number-producing path, not only the challenged number;
6. reconcile all outputs and refresh the complete packet;
7. re-review the complete packet in a fresh reviewer context.

Allow at most two fix-and-re-review rounds after the initial review. Do not automatically accept reviewer findings. If any blocker remains after the second round, stop with `VERDICT: BLOCK`, list the remaining blockers, and keep the analysis local.

**Complete when:** a fresh full review returns `PASS`, or two bounded fix rounds end with the analysis explicitly blocked.

### 6. Release only after PASS

After `PASS`, the driver may create `release-summary.md` from the final reviewed packet. The summary is channel-neutral and contains:

- at most six number-first bullets;
- the denominator and time window for every rate;
- uncertainty or effect size for every inferential claim;
- one material caveat;
- one `So what` line only when the reviewed report directly supports it;
- a report location for every claim so the summary remains evidence-locked.

Each bullet's first non-marker token must be its primary reported number, for example `- 40.0% renewed ...`; a date or label is not number-first.

Use no new calculations, claims, or recommendations. Include no charts, customer identifiers, organization identifiers, unauthorized small cells, or row-level data. Do not post or transmit the summary.

**Complete when:** every summary statement maps to a reproduced claim in the final `PASS` packet and the output contains no prohibited identifier or new inference.

## Terminal states

- **PASS**: zero blockers in a fresh complete review. The report may be shared through the user's normal release process; an optional evidence-locked summary may be written.
- **BLOCK**: one or more blockers remain, required evidence is materially incomplete, or the two-round limit was reached. Keep all release artifacts local.
