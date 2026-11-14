# Review checklist

Apply **Universal** to every analysis. Then apply only the sections matching the recorded analysis shape. A single failed item is a `BLOCKER` when it can change a consequential claim, prevent reproduction, conceal material uncertainty, or disclose sensitive data; otherwise it may be a `NIT`.

## Universal

### Provenance and snapshot integrity

- Identify every source, owner, extraction method, snapshot identifier, freshness date, and timezone.
- Confirm all inputs represent a consistent snapshot or that cross-snapshot timing is disclosed and harmless.
- Confirm source substitutions, backfills, schema changes, and manually supplied values are documented.
- Trace the population from source records to the analytic dataset without an unexplained gap.

### Documentation and reproducibility

- Confirm the packet documents data, code, run command, environment, parameters, and seeds where relevant.
- Regenerate every consequential table, number, and claim from the provided path; flag manual spreadsheet or prose-only transformations.
- Confirm parameter defaults match the report and every material parameter is recorded.
- Reconcile generated outputs to the report and explain any difference.

### Grain, population, and time

- State source grain, post-transformation grain, unit of analysis, eligible population, and exclusion rules.
- Confirm each row represents the intended unit and each unit appears the intended number of times.
- Check inclusive and exclusive date boundaries, timezone conversions, lookback windows, freshness lags, and partial periods.
- Confirm the analysis population and time window match the claim's scope.

### Attrition, missingness, and duplicates

- Record row and unit counts after every material filter, aggregation, and join; explain unexpected loss or gain.
- Quantify missingness for fields used in eligibility, metrics, outcomes, treatments, covariates, and joins.
- Confirm missing values are not silently coerced to zero, false, or an observed outcome.
- Check duplicate records and duplicate analytic units before and after joins; document the deduplication rule.
- Test whether exclusions or missing-data handling materially change the result or represented population.

### Joins and reconciliation

- Declare expected join cardinality and verify key uniqueness on both sides before joining.
- Measure matched, unmatched, and multiply matched units after each material join.
- Reconcile totals and distinct unit counts before and after joins against an independent target.
- Treat an unintended many-to-many join that inflates a consequential count, denominator, or value as a `BLOCKER`.

### Metrics and denominators

- Define every numerator, denominator, unit, aggregation, weighting rule, and zero-denominator behavior.
- Confirm numerator eligibility is a subset of denominator eligibility and both use the stated time window.
- Distinguish users, accounts, events, sessions, orders, and rows; do not substitute one grain for another.
- Confirm totals reconcile to a source-of-truth target or explain the bounded difference.
- For every rate, verify that the displayed denominator and time window match the implemented ones.

### Statistical support and uncertainty

- Confirm the method's assumptions fit the data and are disclosed when consequential.
- Report sample size, effect size, and uncertainty for inferential claims; do not rely on a p-value alone.
- Check dependence, clustering, weighting, skew, outliers, and small samples where they affect uncertainty.
- Distinguish statistical significance from practical importance.
- Expose material uncertainty rather than converting an inconclusive result into a recommendation.

### Claim-to-code lineage and disclosure

- Map every consequential claim and recommendation to a report location, generated output, code or query, and input snapshot.
- Confirm displayed precision does not exceed measurement or estimation precision.
- Distinguish planned analyses and metrics from exploratory or post-hoc findings.
- Account for multiple comparisons where several hypotheses, metrics, segments, or model variants were examined.
- Ensure caveats and corrections remain visible wherever the affected claim appears.
- Bound causal or predictive language to what the design supports.

### Privacy and release safety

- Use the minimum data necessary; prefer aggregates, schemas, dictionaries, metadata, and reproducible local queries.
- Confirm row-level data is authorized and necessary before including it in any review context.
- Remove customer names, organization names, direct identifiers, secrets, and unnecessary quasi-identifiers.
- Check small cells, rare combinations, free text, and linked attributes for re-identification risk.
- Confirm outputs obey applicable consent, retention, contractual, and access boundaries.
- Treat any material risk of sensitive-data disclosure as a `BLOCKER`.

## Churn or retention

- Define cohort entry, retention observation, churn event, return event, and the analytic unit.
- Require full opportunity to reach each reported horizon. Exclude or explicitly censor immature cohorts rather than counting them as non-retained.
- Treat immature cohorts included in a mature-period denominator as a `BLOCKER` when they can change the result.
- Check right-censoring at the source snapshot and left-censoring from incomplete history.
- Distinguish `canceled_at`, access or contract `ended_at`, non-renewal, failed payment, downgrade, and inactivity; use the event matching the claim.
- Define reactivation or resurrection and prevent a returned customer from being inconsistently counted as both churned and retained.
- Account for competing events such as deletion, migration, plan change, or ineligibility.
- Confirm cohort calendars, grace periods, renewal intervals, and observation windows are consistent across cohorts.
- Compare mature cohort sizes and attrition by cohort to detect changing eligibility or instrumentation.

## Funnel

- Define eligibility and unit of analysis at every step; state when and why the denominator changes.
- Enforce event ordering. A later-step event before an earlier step does not satisfy an ordered funnel unless explicitly defined.
- Define the conversion window and exclude or censor entrants without a full opportunity to convert.
- Deduplicate retries, repeated events, refreshes, and idempotent writes using a documented rule.
- Verify identity stitching across anonymous, logged-in, device, user, and account identifiers without merging unrelated units.
- Account for users entering more than once, skipping steps, taking parallel branches, or changing eligibility.
- Check instrumentation version, event loss, delayed arrival, and backfills across compared periods.
- Reconcile step counts to independent eligible-population and event-volume targets.

## Controlled experiment

- Verify the randomization unit, analysis unit, and variance estimator agree; account for clustering and repeated observations.
- Run a sample-ratio-mismatch check overall and for material assignment strata before interpreting outcomes.
- Treat unexplained SRM as a `BLOCKER`; investigate assignment, triggering, filtering, eligibility, telemetry, and join loss rather than merely adjusting the final ratio.
- Confirm exposure and triggering rules are pre-treatment, consistently logged, and do not condition on an outcome or treatment effect.
- Check assignment leakage, crossovers, contamination, interference, and concurrent experiments.
- Record the preselected primary metric, guardrails, hypothesis, population, duration, and analysis plan; label post-hoc work.
- Confirm prospective power or minimum detectable effect, planned sample size, and whether achieved precision can support the claim.
- Verify the stopping rule. Repeatedly inspecting a fixed-horizon test and stopping at significance is a `BLOCKER` unless valid sequential inference or an alpha-spending design was specified and used.
- Correct or bound multiplicity across metrics, variants, segments, repeated looks, and model choices.
- Report absolute and relative effect sizes with confidence intervals and practical significance.
- Check delayed outcomes, novelty or primacy effects, carryover, seasonality, and sufficient experiment duration.
- Review guardrails and adverse effects even when the primary metric improves.

## Observational or causal

- State the estimand, treatment or exposure, outcome, target population, time zero, and follow-up period.
- Identify plausible common causes and explain the adjustment set; avoid adjusting by availability alone.
- Check selection, survivorship, missing follow-up, and loss to follow-up for dependence on exposure or outcome.
- Do not condition on colliders, mediators, or other post-treatment variables unless the estimand requires and justifies it.
- Verify temporal ordering and address reverse causality.
- Check positivity or overlap and show where estimates rely on extrapolation.
- Match standard errors and uncertainty to weighting, matching, clustering, repeated measures, or model selection.
- Test sensitivity to material modeling choices, unmeasured confounding, missingness, and influential observations.
- Use causal language only when identification assumptions are stated, plausible, and supported; otherwise describe association.

## Cost, pricing, or margin

- Identify the authoritative revenue and cost sources, accounting basis, recognition period, and reconciliation target.
- State the allocation basis for shared costs and test whether the conclusion depends on that basis.
- Separate fixed, variable, step, sunk, and one-time costs; do not present allocated fixed cost as marginal cost.
- Account for refunds, credits, discounts, chargebacks, taxes, fees, rebates, and deferred or accrued amounts.
- Normalize currency with the stated exchange-rate source and date; do not mix nominal currencies or periods.
- Distinguish bookings, billings, gross revenue, net revenue, cash collected, and recognized revenue.
- Define gross margin and contribution margin explicitly and include only costs appropriate to the named measure.
- Separate blended average economics from marginal or incremental economics.
- Check volume, mix, tiering, minimum commitments, and nonlinear pricing assumptions.
- Reconcile totals to the ledger or other source of truth and explain every material residual.

## Sources

- [JASA Reproducibility Review Form](https://jasa-acs.github.io/repro-guide/pages/review-form.html)
- [American Statistical Association Ethical Guidelines for Statistical Practice](https://www.amstat.org/docs/default-source/amstat-documents/EthicalGuidelines.pdf?v=0525)
- [Kohavi et al., Practical Guide to Controlled Experiments on the Web](https://ai.stanford.edu/~ronnyk/GuideControlledExperiments.pdf)
- [Fabijan et al., Diagnosing Sample Ratio Mismatch in Online Controlled Experiments](https://exp-platform.com/Documents/2019_KDDFabijanGupchupFuptaOmhoverVermeerDmitriev.pdf)
