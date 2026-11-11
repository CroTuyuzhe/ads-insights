# Bidding Strategy Decision Guide

Use this guide when a recommendation could change base bid, bidding strategy, placement multipliers, schedule-based bid rules, or budget. The goal is to select the control layer that matches the diagnosed problem without destroying qualified exposure.

## 1. Separate the bid stack

Treat these as distinct controls:

1. **Base bid:** the shared starting bid for the target or traffic pool.
2. **Placement multiplier:** a placement-specific adjustment for Top of Search, Rest of Search, or Product Pages where supported.
3. **Schedule-based bid rule:** a time- or date-specific adjustment that can change the bid across hours or days.
4. **Bidding strategy:** determines whether Amazon may adjust the eligible bid using predicted conversion likelihood.
5. **Paid CPC:** an auction outcome summarized across the clicks actually won; it is not the same as any one configured bid.

Do not describe a configured base bid or placement-adjusted bid as the final CPC. A fixed-bid campaign can still show changing average CPC because auction competition, search-term mix, placement mix, and scheduled adjustments change. Its average CPC can also exceed the raw base bid when placement or schedule adjustments raise the eligible bid.

Before diagnosing a CPC change, reconcile the live values for all four configurable layers. Use the current Amazon Ads console for current settings and exported reports for performance. Verify current Amazon documentation before quoting numeric platform adjustment limits because those limits can change.

## 2. Choose the bidding strategy by campaign role and failure mode

| Strategy | What it controls | Stronger candidate when | Main risk |
|---|---|---|---|
| Fixed | Holds the configured eligible bid instead of applying conversion-probability-based dynamic changes | Qualified exposure or rank continuity is the priority; targets are tightly controlled; the seller accepts paying consistently across eligible auctions | Weak auctions are not selectively discounted; more delivery does not guarantee efficient conversion |
| Dynamic down only | Allows Amazon to reduce bids for auctions predicted less likely to convert | Broad, auto, category, or other mixed discovery traffic needs more auction selectivity; budget or efficiency control matters; CPC is not the only broken metric | Exposure can shrink; lower CPC does not guarantee better traffic or higher CVR |
| Dynamic up and down | Allows Amazon to raise or lower bids according to predicted conversion likelihood | A proven target has stable CVR, adequate margin and budget, and the explicit goal is qualified scaling or rank support | CPC and spend can expand quickly; prediction quality and placement overlap can create volatility |

These are candidates, not universal role assignments. Campaign history, account-specific results, margin, placement economics, and current platform behavior override generic defaults.

## 3. Route the diagnosis to the correct lever

- **CPC rises while CVR remains healthy:** inspect auction cost and placement mix. A base-bid or inefficient placement reduction may fit; a strategy switch is not automatically required.
- **CPC is stable or falls while CVR collapses:** do not call the cheaper clicks an improvement and do not reflexively cut the base bid. Check search-term or ASIN mix, placement mix, offer and listing conversion, and external events. For mixed discovery traffic, a fixed-to-down-only switch with the base bid held constant can be tested as an auction-selectivity hypothesis.
- **Impressions are high but CTR is weak and clicks are already sparse:** lowering the base bid can make the sample non-viable without solving relevance. Inspect query, target, image, offer, and placement relevance first.
- **Impressions and clicks are low, the target is core, and paid CPC repeatedly approaches the relevant effective-bid ceiling:** test whether bid rank or an auction threshold suppresses delivery. Raise only the bid layer tied to the desired placement, define a target CPC and required CVR, and use a click or no-order spend cap. Do not require the weak sparse-period CVR to be healthy before running this bounded test when historical conversion makes the required CVR credible.
- **Only one placement is uneconomic:** change that placement control before suppressing the whole target.
- **Only certain hours are uneconomic:** change the schedule rule before changing the all-day base bid.
- **The campaign does not exhaust its budget:** budget is not the active delivery constraint. Do not present a budget change as a CPC, CVR, or ACoS fix.
- **The campaign exhausts its budget while profitable traffic is suppressed:** budget can be a scaling or allocation lever, but only after confirming the traffic is economically qualified.

## 4. Run a strategy-switch experiment

For an ordinary switch between fixed, down-only, and up-and-down:

1. Record the exact modification timestamp and the live base bid, budget, placement multipliers, schedule rules, targets, and negatives.
2. State the mechanism being tested. Example: `down-only may discount low-conversion-probability auctions in a mixed discovery pool while preserving the maximum base bid for stronger opportunities`.
3. Hold base bid, placements, schedule rules, and budget constant when practical. If another setting must change, state that attribution will be ambiguous.
4. Compare a stable pre-change baseline with complete post-change days. Use a minimum-click or minimum-spend evaluation point for low-volume campaigns instead of relying only on calendar days.
5. Define an exposure floor from recent qualified impressions and clicks, a maximum incremental-loss limit, a keep rule, and an exact rollback to the prior strategy.
6. If the strategy fails, diagnose the failure at search-term, customer-ASIN, or placement grain before applying another blanket base-bid cut.

Do not declare success from CPC alone. Interpret the joint outcome:

| Post-change result | Interpretation |
|---|---|
| CPC falls, CVR and order rate hold or improve, economics improve, exposure stays above floor | Consistent with a successful strategy change |
| CPC falls but CVR deteriorates | Cheaper traffic is not better traffic; inspect mix and conversion |
| CPC falls and exposure breaches the floor | The intervention may be suppressing delivery; apply the predefined rollback |
| CPC stays similar but CVR and economics improve | The switch can still be successful; CPC reduction was not the objective by itself |
| Exposure holds but adequate clicks still produce too few orders | Strategy did not solve relevance or offer conversion; use lower-grain controls |

## 5. Interaction rules

- Fixed bidding does not neutralize placement multipliers or schedule-based bid rules.
- Dynamic bidding adds another adjustment layer; a placement multiplier is not the final auction bid or expected CPC.
- Raising a base bid strengthens every eligible placement; raising one placement multiplier is more selective.
- A bid increase can change observed CVR indirectly by changing eligibility, placement, sub-position, and traffic mix. It can improve or dilute conversion; never present CPC itself as the direct conversion mechanism.
- Lowering a base bid under fixed bidding does not selectively remove only poor traffic. It can reduce both qualified and unqualified exposure.
- Switching to down-only is a test of auction selectivity, not a promise of lower CPC, higher CVR, or lower ACoS.
- Do not use the daily budget to control efficiency when the campaign is already spending below budget.

## 6. Current evidence boundary

The distinction between configured bid and paid CPC is platform mechanics. The performance claims above remain testable operating hypotheses. Preserve counterexamples and only promote them after repeated, adequately sampled results across products and traffic roles.
