# Provisional Decision Rules

These are starting hypotheses, not universal Amazon thresholds. Calibrate by product price, margin, campaign role, historical conversion rate, and traffic variance.

## 1. Establish economic limits

Calculate:

- `Target CPA = AOV x target ACoS`
- `Maximum CPC at observed CVR = AOV x CVR x target ACoS`
- `Break-even CPC at observed CVR = AOV x CVR x break-even ACoS`
- `Required CVR at current CPC = CPC / (AOV x target ACoS)`

If required CVR materially exceeds the product's credible historical CVR, the current CPC or traffic mix cannot support the target ACoS.

## 2. Use sample-aware evidence

Preferred decision units:

- High-volume unit: at least 2-3 comparable days and roughly 40-60 clicks for directional changes.
- Normal-volume unit: 7 days or roughly 20-40 clicks.
- Sparse unit: 14-30 days, or spend relative to target CPA.

For a no-order unit, use expected conversions:

`Expected orders = clicks x reference CVR`

`P(zero orders) = (1 - reference CVR) ^ clicks`

Zero orders becomes stronger negative evidence once expected orders reach about 2-3. This is still a heuristic; strategic relevance and query intent matter.

A spend or click loss cap answers how much risk the seller accepts; it does not prove the traffic has structurally failed. Keep the financial stop and the statistical evidence threshold separate. For example, at 5% CVR, 30 clicks still have about a 21.5% chance of zero orders.

## 2A. Triage recent changes before waiting

Separate **loss containment** from **settled conversion assessment**.

Run an immediate next-day risk check whenever a bid, placement, budget, targeting, negative, or campaign-structure change was made:

1. Compare actual spend with the user's daily cap and the unit's loss ceiling.
2. Compare impressions, clicks, CPC, CTR, CVR, orders, and spend with the stable baseline.
3. Identify the newest reversible expansion and calculate its effective-bid or click-capacity change.
4. Compare sibling campaigns for a simultaneous traffic spike, but do not let a shared market event excuse an unacceptable loss.

Use one of these decisions:

- **Keep now:** current economics are acceptable and leading metrics remain inside the declared guardrails.
- **Rollback one step now:** a recent expansion is followed by a material spend or exposure surge plus a conversion collapse or severe ACoS breach.
- **Cap now, diagnose later:** attribution is incomplete, but continued delivery can exceed the daily budget or maximum acceptable loss.

Prefer reversing the most recent reversible expansion first, such as restoring a placement multiplier to its previous value. Preserve unchanged bids and placements when possible so the rollback remains interpretable.

Attribution delay is a confidence modifier, not a veto on action. It can justify a smaller rollback or temporary cap instead of a full pause, but it cannot justify unlimited continued spend.

Do not write “wait another day” unless all of the following are stated:

- Current incremental loss is bounded and acceptable.
- No user-defined budget cap has been breached.
- The latest leading indicators have not materially violated their guardrails.
- A specific review point and automatic next decision are defined.

## 2B. Reset after a customer-visible offer change

When price, Prime or member discount, coupon, deal badge, Buy Box, or delivery promise changes:

1. Verify the new offer on the customer-facing page and record its visible timestamp as `T0`.
2. Treat the calendar day containing `T0` as a transition day, not a clean before-or-after sample.
3. If loss is bounded, hold bids, placements, targeting, budgets, and bidding strategy constant through the first complete post-`T0` day.
4. Use the first complete day to judge impressions, CTR, and clicks. Treat CVR, orders, CPA, and ACoS as directional because attribution and sample may still be incomplete.
5. Judge conversion recovery after an adequate cumulative click sample or two to three complete days, whichever better fits the unit's volume.
6. If an offer failure remains live, do not raise bids to compensate for the resulting traffic loss unless the seller explicitly accepts the weaker economics.

## 3. Bid changes

### Classify the direction before choosing the percentage

Do not begin with “raise or lower the bid.” First classify the unit:

| Direction | Stronger evidence |
|---|---|
| Mature scale | Current CVR and ACoS are healthy, qualified volume is constrained, and the target or placement has enough margin for CPC inflation |
| Auction-threshold scale test | Core relevance or historical conversion is strong; current delivery is thin; paid CPC is near the full effective-bid ceiling; budget, offer, eligibility, and indexing are not the constraint; a higher auction tier could plausibly change position or traffic quality |
| Keep | Delivery and economics fit the campaign role, or a current experiment remains inside its declared guardrails |
| Controlled contraction | Adequate exposure already exists; lower-grain traffic is structurally weak or an expansion failed; the expected saving or traffic-quality benefit is material enough to justify the lost click capacity |
| Stop or isolate | The unit is irrelevant, repeatedly uneconomic after adequate samples, or has a healthier lower-grain destination that can preserve qualified demand |

Calculate how tightly delivery is pressing against the configured ceiling:

`Ceiling utilization = observed paid CPC / placement-adjusted effective bid`

Repeated utilization near 1.0 is not proof of an auction threshold, but together with low delivery and strong relevance it supports a scale test. A bid reduction in this state can drop the unit below the clearing range and cause nonlinear exposure loss. Conversely, low utilization suggests that bid rank may not be the active constraint.

### Trim

Start with a 5-10% decrease when:

- CPC exceeds the economically supportable level, or
- a recent bid increase coincides with a material exposure expansion and degraded CTR or CVR, or
- a unit has adequate clicks and ACoS materially exceeds target.

Use 10-20% only when evidence is strong and exposure is already abundant. Avoid large cuts on low-impression units.

Define an exposure floor from the last efficient phase, such as:

- Minimum daily impressions.
- Minimum daily clicks.
- Minimum seven-day orders.
- Minimum share of top converting placement or search terms.

If the floor breaks while quality remains healthy, restore one step, not necessarily the entire previous bid.

### Scale

Start with a 3-8% increase when:

- CVR meets or exceeds its healthy reference.
- ACoS is below target with enough buffer for auction inflation.
- Budget or bid rank visibly constrains qualified volume.

Do not scale after one good order. Watch for nonlinear auction thresholds: a small bid increase can unlock a disproportionate volume of lower-quality impressions.

For mixed campaigns, require the proposed target or subgroup's own economics and bid history. A healthy campaign total does not justify crossing a target-level bid that previously produced diluted traffic.

### Auction-threshold scale test

Use a scale test when ordinary Scale criteria are not yet met but continued holding cannot answer whether the current bid buys the wrong auction tier. Require all of the following:

- The query, ASIN, or target is core, highly relevant, historically converting, or strategically necessary for rank support.
- Impressions or clicks are materially below the useful operating range.
- The customer-visible offer, inventory, Buy Box, indexing, and budget are healthy enough that more bid can actually change delivery.
- Paid CPC is close to the relevant effective-bid ceiling, or recent bid history shows threshold-like exposure response.
- The seller accepts a bounded test loss, and the target can be controlled without raising unrelated weak placements or siblings.

Design the test:

1. Change one bid layer that maps to the desired traffic, such as Rest of Search rather than the shared base bid when Product Pages should not expand.
2. Select a meaningful but reversible effective-bid increase. A provisional 5-12% step is often more diagnostic than a token 1-3% change, but calibrate to historical thresholds and console granularity.
3. Calculate the target paid-CPC range and `required CVR = test CPC / (AOV x target ACoS)`. The required CVR must be historically credible even if the current sparse sample is weak.
4. Define an exposure objective, such as a minimum impression or click increase, plus a minimum click sample and maximum no-order spend.
5. Keep only when delivery improves and observed CVR rises enough to absorb the higher CPC. If CPC rises without the planned exposure or conversion response, roll back exactly one step.

Do not describe this as “raising CPC to improve conversion.” The mechanism being tested is whether higher eligibility wins a better placement, sub-position, or query mix. Record contradictory outcomes because a higher bid can also unlock lower-quality marginal traffic.

### Effective-bid check

For placement multiplier `m`:

`Effective bid = base bid x (1 + m)`

Report both base and effective changes. A 5% base-bid cut combined with a placement increase may not be a cut at that placement.

Before calculating a pre/post change, reconcile the actual values on both sides of the intervention. Exported placement rows may repeat the latest configured multiplier across historical performance dates; treat the user's timestamped live-console confirmation or a dated change ledger as the source of truth for settings. Historical delivered metrics remain usable, but a repeated current-setting field is not bid history.

To preserve a placement's configured effective bid when the base bid changes from `b_old` to `b_new`, solve the multiplier on the whole bid stack:

`m_new = [b_old x (1 + m_old) / b_new] - 1`

If `b_new = b_old x (1 - r)`, the unrounded shortcut is:

`m_new = (1 + m_old) / (1 - r) - 1`

Do not multiply only the displayed placement percentage by the reciprocal of the base-bid change. After rounding the base bid and multiplier to console-supported values, recalculate each placement's old and new effective bid and report the residual percentage change. This prevents both under-compensation and duplicate compensation.

A Product Pages adjustment of `0%` removes the positive multiplier; it does not disable Product Pages delivery. Lowering the shared base bid while compensating search placements can intentionally reduce Product Pages effective bids while approximately preserving Top of Search and Rest of Search. Classify this as a modeled traffic-allocation change and evaluate each placement after the next complete post-change day.

### Shared-control impact check

Before changing a campaign-wide placement multiplier, budget, or bidding strategy, build a compact impact table for every material ad group or target that shares that control. If the loss is concentrated in one child unit while a sibling is healthy, use the child's own bid, query, target, or ASIN control first. Do not change a shared placement merely because the campaign-level placement is weak when subgroup-by-placement attribution is unavailable.

### Bid-saving materiality check

For a proposed fractional effective-bid reduction `r`, estimate the maximum short-window saving before assuming it will improve ACoS:

`expected saving = expected clicks x current CPC x r`

Also estimate the click capacity and order cadence at risk. When CPC is stable, CVR is the broken link, and a small reduction saves only a trivial amount relative to target CPA while the campaign already takes several days to accumulate an order-sized click sample, preserve the current bid and use a bounded click test or a lower-grain control. A small saving is not sufficient justification for making the experiment statistically slower.

Apply the same materiality check to conservative inaction. If a core target is accumulating too few clicks to sustain its expected order cadence and a bounded increase has a credible auction-threshold mechanism, indefinite holding is not neutral; it preserves under-delivery and delays learning. Quantify the cost and risk of Hold alongside the cost and risk of Scale test.

## 4. Placement changes

- Compare placement CPA, CVR, and ACoS with adequate clicks.
- Increase a placement only if its conversion advantage can absorb the higher effective CPC.
- Reduce the inefficient multiplier before suppressing the entire target when other placements remain healthy.
- Avoid changing base bid and multiple placement multipliers together unless modeling the resulting effective bids.

## 5. Search terms and product targets

### Harvest

Move a query or ASIN into controlled exact or product targeting when it has repeated orders, acceptable economics, and sufficient relevance. Prevent duplicated uncontrolled bidding where practical.

### Negate or pause

Consider when:

- The term or ASIN is clearly irrelevant, regardless of click count.
- It reaches roughly 2-3 target CPA of spend without orders.
- It accumulates enough clicks that zero orders is inconsistent with the reference CVR.
- It repeatedly converts below the economic threshold across comparable periods.

Do not negate relevant exploration solely due to a short zero-order streak. Lower or isolate it with a bounded test first.

### Category and auto ASIN containment

When one customer ASIN is weak inside a mixed category or auto target:

- Keep the shared campaign settings unchanged when they also buy proven ASINs efficiently.
- Prefer isolation for a converting but uneconomic ASIN when retaining learning or future recovery matters.
- If the seller explicitly does not want a separate target and the ASIN has adequate clicks, spend, or repeated poor economics, an exact ASIN negative is a valid reversible containment action.
- Record whether the ASIN had historical orders. Negating a converting ASIN is a deliberate volume-for-efficiency trade, not evidence that it was irrelevant.
- Do not infer that every ASIN shown in a search-term report came from Product Pages without a matched placement report.

## 6. Budget decisions

- Increase budget only when qualified demand is being capped and marginal economics are acceptable.
- Do not use more budget to solve poor CTR or CVR.
- Do not reduce budget to improve CPC or traffic quality when the campaign or portfolio is not budget constrained. Budget is a delivery cap; use target, query, ASIN, bid, or placement controls for traffic economics.
- If a campaign runs out early, distinguish whether profitable targets or waste consumed the budget.
- Reallocate from structurally weak discovery to proven harvest before raising total spend.
- Calculate `click capacity = daily budget / expected CPC` and `expected orders = click capacity x reference CVR` before a material budget cut.
- Approximate the chance of a zero-order day as `(1 - reference CVR) ^ click capacity`. Use this as a volatility warning, not a promise.
- For mature order-producing campaigns, preserve a minimum viable daily click sample and order cadence. Prefer 5-10% steps unless the campaign is structurally broken or the user explicitly accepts volume loss.
- Do not cut budget and effective bids together unless the intended combined contraction is modeled by placement.

## 7. Promotions and deal endings

Segment pre-deal, deal, and post-deal periods. At deal end:

- Recalculate required CVR at the restored price and expected CPC.
- Expect traffic and conversion mix to normalize; do not overreact to the first partial day.
- Preserve proven core terms and targets.
- Reduce promotional spillover or marginal discovery gradually.
- Use total sessions, total unit-session percentage, total sales, and contribution profit when available.
- Verify the actual front-end price and badge; a promotion can expire or fail while campaign settings remain unchanged.
- Calculate the AOV gain and observed CVR loss separately. A higher price helps ACoS only if conversion and click-through deterioration do not overwhelm the higher revenue per order.
- Start a new phase at the exact offer correction time. Keep ads unchanged for the first complete post-reset day when risk is bounded so offer recovery is not confounded with bid changes.

## 7A. Rank-support traffic recovery

Advertising can support qualified order velocity but cannot guarantee organic or category-rank recovery. Before a traffic sprint:

- Resolve customer-visible offer failures first.
- Estimate the daily order gap from total product orders, not advertising orders alone.
- Convert the order gap into required clicks with `required incremental clicks = incremental orders / credible CVR`.
- Convert clicks into spend with `incremental spend = required incremental clicks x expected CPC`.
- Scale proven targets first and keep mixed discovery bounded.
- Stage expansion rather than changing every campaign at once. Preserve a control group or at least one unchanged high-volume campaign when practical.
- Stop or roll back when exposure expands materially without proportional clicks or orders.

## 8. Provisional traffic-health signals

Use relative baselines before fixed percentages:

- CTR deterioration: a drop of roughly 25% or more versus a comparable efficient phase can indicate traffic dilution.
- CVR deterioration: a drop of roughly 25-35% with adequate clicks is material.
- Exposure shock: impressions increasing by more than roughly 50-100% without proportional clicks or orders can indicate entry into a broader auction pool.
- CPC stability band: within roughly 10% while CTR or CVR collapses shifts attention toward mix and conversion causes.

These signals trigger investigation, not automatic bid changes.

## 9. Monitoring cadence

### One-day health check

Check delivery, budget, CPC spikes, Buy Box, inventory, catastrophic exposure loss, and post-change spend or CVR failure. Reverse operational failures and recent expansions that breach their declared loss, exposure, or conversion guardrails; do not wait for settled ACoS when continued spend is unsafe.

### Three-day directional check

When clicks are sufficient, compare impressions, CTR, CPC, spend, and search or placement mix. Preserve the change if movement is within the predefined band.

### Seven-to-fourteen-day decision

Judge CVR, CPA, ACoS, orders, and organic or total-sales effects. Extend the window for sparse traffic or attribution lag.

## 10. Keep is a valid action

Recommend Keep when:

- Economics meet the role-specific target.
- Traffic quality is stable.
- Volume is sufficient for the role.
- No structural leak is evident.

Specify the monitoring threshold that would cause reconsideration.

Keep is not valid solely because:

- The latest day may receive additional attribution.
- Causality is uncertain.
- The unit performed well before the newest change.
- More data would always be useful.

When current data is poor, Keep requires a quantified loss cap and positive evidence that the unit remains inside its role-specific guardrails.
