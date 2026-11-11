# Output Template

## Executive diagnosis

- **Fact:** [measured change with comparable dates]
- **Inference:** [most likely mechanism and confidence]
- **Decision:** [immediate action and why]

## Reconciled current state

| As of | Unit | Budget | Base bid | Strategy | Top | Rest | Product Page | Active negatives | Last completed action | Source |
|---|---|---:|---:|---|---:|---:|---:|---|---|---|
| [timestamp] | [campaign or target] | | | | | | | | | Live console, user confirmation, or export |

Resolve conflicts before recommending changes. User-confirmed live settings outrank stale report fields. Mark every recommendation as new, already completed, rejected, or superseded.

## Immediate risk decision

- **Status:** Acceptable, controlled concern, or urgent rollback.
- **Today's action:** Keep, mature scale, bounded scale test, rollback one step, cap spend, trim, isolate, or stop. Never use “observe” as the action.
- **Loss at risk:** Current spend versus daily cap, target CPA, or declared loss ceiling.
- **Newest reversible change:** Exact old value and current value.
- **Attribution handling:** State whether incomplete attribution changes the rollback size, not whether risk containment is required.

## Evidence table

| Unit and role | Period | Bid or setting | Impressions | CTR | CPC | CVR | CPA | ACoS | Orders |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|
| [campaign or target] | [baseline] | [value] | | | | | | | |
| [campaign or target] | [evaluation] | [value] | | | | | | | |

Always calculate ratios from summed numerators and denominators.

## Root-cause assessment

| Candidate cause | Evidence for | Evidence against or missing | Confidence |
|---|---|---|---|
| [cause] | [facts] | [alternative evidence] | High, medium, or low |

## Quantified action table

| Unit | Role | Urgency | Decision today | Current | Proposed | Change | Reason | Exposure floor | Loss cap | Success rule | Rollback rule | Review point |
|---|---|---|---|---:|---:|---:|---|---|---|---|---|---|
| [unit] | [role] | Normal, controlled, opportunity, or urgent | Keep, mature scale, scale test, rollback, cap, trim, isolate, or stop | | | | | | | | | |

Include unchanged units as Keep rows.

## Follow-up checks

First record the action the user actually implemented. If it differs from the recommendation, update the baseline and evaluate the implemented action rather than the discarded proposal.

### Next day

- Verify impressions and clicks did not fall below the exposure floor.
- Verify CPC, budget delivery, inventory, and Buy Box.
- Check spend against the user's cap and compare the newest change with its rollback guardrail.
- Contain severe loss immediately even when conversion attribution is incomplete; defer only the final structural diagnosis.

### Three days or minimum sample

- Compare traffic quantity and quality with the baseline.
- Check whether search-term, ASIN, or placement mix changed.
- Apply the predefined keep or rollback rule.

### Seven to fourteen days

- Judge CVR, CPA, ACoS, orders, total sales, and organic effects.
- Separate promotion and non-promotion periods.
- Promote, revise, or reject the hypothesis.

## Missing evidence

List only evidence that could change the decision, for example:

- Search-term or product-target report.
- Placement report.
- Change history.
- Actual price, coupon, deal, Buy Box, inventory, or review timeline.
- Business report and organic-rank trend.
- Margin and target ACoS.

## Hypothesis ledger

| ID | Hypothesis | Product and context | Evidence so far | Counterevidence | Status | Next validation |
|---|---|---|---|---|---|---|
| H-001 | [testable statement] | [scope] | [observations] | [observations] | Proposed, supported, rejected, or promoted | [data and threshold] |

Do not generalize from one product. Promote a heuristic only after repeated tests across multiple products or clearly comparable contexts.
