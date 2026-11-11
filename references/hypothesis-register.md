# Hypothesis Register

This register contains plausible, testable advertising heuristics derived from limited observations. It is deliberately not a rulebook. Preserve counterexamples and scope every result to product, traffic type, marketplace, price band, and promotion state.

## Status definitions

- **Proposed:** plausible but supported by too little evidence.
- **Provisionally supported:** repeated within one product or one context.
- **Cross-context supported:** repeated across several products or materially different contexts.
- **Rejected:** evidence consistently contradicts the hypothesis.
- **Conditional:** useful only under documented conditions.

## Current hypotheses

| ID | Hypothesis | Current status | Evidence needed | Key counterchecks |
|---|---|---|---|---|
| H-001 | A small bid increase can cross an auction threshold and create a nonlinear increase in impressions with worse CTR or CVR. | Proposed | Daily target-level bid history plus placement and search-term or ASIN mix across several interventions | Demand spike, placement change, deal traffic, budget release, indexing, competitor changes |
| H-002 | A modest bid decrease can improve average traffic quality by surrendering marginal auctions, but only while qualified exposure remains above a defined floor. | Proposed | Pre/post bid phases with equivalent promotion state and adequate clicks | Lower bid may simply reduce all traffic; Amazon does not guarantee better relevance at lower bids |
| H-003 | When CPC changes little but CTR and CVR deteriorate materially, traffic composition or offer conversion is usually more important than click-cost inflation. | Proposed | Search-term, target, placement, listing, and offer evidence | Attribution lag, day-of-week effects, competitor promotion, Buy Box or inventory issue |
| H-004 | Deal or coupon periods do not necessarily improve aggregate CTR and CVR because broader reach and price-sensitive browsing can dilute the traffic mix. | Proposed | Pre-deal, deal, and post-deal advertising plus business reports across products | Actual discount depth, badge visibility, competitor promotions, stock and review changes |
| H-005 | Exposure protection should be part of every bid reduction: evaluate impressions and clicks before waiting for final ACoS. | Provisionally supported as an operating safeguard | Repeated tests showing exposure floors prevent order collapse without preserving waste | Exposure alone is not value; the floor must be qualified and role-specific |
| H-006 | Repeated bid, placement, budget, and targeting changes inside a short window make causal diagnosis unreliable and can produce unnecessary reversals. | Proposed | Change histories linked to stable control periods | Urgent operational failures may require overlapping corrections |
| H-007 | Auto and broad discovery perform better as bounded feeders to isolated harvest campaigns than as large undifferentiated spend pools. | Proposed | Search-term migration and marginal-profit analysis across products | Some low-volume products may need consolidated structures for delivery |
| H-008 | A target with healthy economics should often be kept unchanged; frequent optimization can destroy a stable baseline. | Proposed | Change-versus-hold comparisons over multiple cycles | Market conditions can change even without edits |
| H-009 | Separating a proven search term from a mixed campaign can release suppressed rotation while keeping bid and placement economics comparable. | Proposed | Before/after search-term exposure and placement mix after isolation | New campaigns may reset delivery or create self-competition |
| H-010 | A layered bid architecture from auto or upper term to broad or phrase to exact can buy incremental exposure at different auction probabilities without relying on one high bid. | Proposed | Query-level overlap, effective CPC, incremental orders, and total account spend | Duplicate eligibility can raise internal auction pressure or merely shift attribution |
| H-011 | A low base bid plus placement multiplier can isolate a placement more cleanly than raising the shared base bid. | Conditional | Placement reports, effective-bid calculations, and adequate clicks by placement | Dynamic bidding, ROS controls, and spillover prevent perfect isolation |
| H-012 | Scaling by campaign split can increase rotation for a suppressed target even when bid and placement stay similar. | Proposed | Stable-market split tests with query-level impression and order data | Demand change, campaign-history effects, and budget release |
| H-013 | Investment advertising creates value only when qualified intervention volume is sufficient and organic or total-sales movement remains observable. | Proposed | Keyword rank, total sales, TACOS, ad orders, and intervention volume | Organic movement may come from price, promotion, seasonality, or competitor changes |
| H-014 | Keyword and ASIN coverage gaps are best found by reconciling competitor relevance, own existing coverage, search volume, and current natural or paid position. | Proposed | Repeated gap launches with incremental performance | Competitor coverage does not guarantee fit for the product |
| H-015 | After a recent traffic expansion, a one-step rollback or spend cap is safer than unconditional observation when spend breaches the user's cap and conversion collapses on meaningful clicks. Attribution lag should change rollback size, not eliminate loss containment. | Proposed | Repeated next-day intervention cases with final attributed outcomes and counterfactual controls | Shared demand spikes, late attribution, price or listing events, and normal daily conversion variance |
| H-016 | In a mixed category target, containing an adequately sampled weak customer ASIN at the ASIN level preserves healthy traffic better than cutting the shared budget or base bid. Isolation preserves optionality; exact negative is the deliberate alternative when the seller declines extra structure. | Proposed | Pre/post ASIN mix, campaign exposure, orders, ACoS, and total-spend outcomes after several containment cycles | The whole category pool may be weak, negative targets may remove incremental orders, and overlap or placement changes may explain the result |
| H-017 | When CPC falls only modestly but CVR collapses in a fixed-bid discovery campaign, switching to dynamic down only while holding base bid and other bid layers constant may improve auction selectivity more cleanly than another blanket base-bid cut. | Proposed | Pre/post strategy-switch phases with search-term, placement, exposure, CPC, CVR, orders, and ACoS data across several campaigns | Down-only may merely reduce exposure; traffic or offer deterioration may persist; Amazon prediction quality and concurrent market changes may dominate |
| H-018 | Expiry of a customer-visible Prime, member, coupon, or deal price can reduce both CTR and CVR even when CPC is stable or lower; restoring the offer before changing bids produces a cleaner diagnosis. | Proposed | Exact front-end offer timestamps plus pre-expiry, failed-offer, and post-restoration advertising and business-report phases | Competitor changes, rank loss, seasonality, Buy Box, delivery, and query or placement shifts |
| H-019 | A campaign's healthy aggregate ACoS does not justify raising a specific target or auto subgroup whose own historical bid phase produced traffic dilution. | Proposed | Target-level daily bid, exposure, CTR, CVR, orders, and search-term or ASIN mix across repeated bid steps | Aggregate may accurately represent the subgroup when it dominates spend and mix is stable |
| H-020 | A click or spend loss cap can be reached while zero orders remains statistically plausible; risk containment and evidence of structural conversion failure require separate thresholds. | Proposed | Repeated low-volume campaigns with reference CVR, click samples, final attributed orders, and intervention outcomes | Nonstationary CVR, attribution lag, and financially intolerable spend may still require earlier containment |
| H-021 | For a core, historically converting target with thin delivery and paid CPC near its placement-adjusted effective-bid ceiling, a bounded effective-bid increase can cross an auction threshold and improve qualified exposure; observed CVR may improve if the new tier has better position or intent, but can deteriorate if the increase unlocks marginal traffic. | Proposed | Pre/post tests with live bid stack, paid CPC, placement, impressions, clicks, search terms, CVR, orders, and rollback outcomes across products | Demand decline, offer or indexing problems, budget limits, placement mix, attribution lag, and higher bids buying broader rather than better traffic |

## Evidence entry format

Append evidence in this form:

| Date | Hypothesis ID | Product and marketplace | Campaign role | Intervention | Baseline sample | Evaluation sample | Result | Confounders | Supports or contradicts |
|---|---|---|---|---|---|---|---|---|---|
| YYYY-MM-DD | H-000 | Generic product label | Harvest, discovery, defense, competitor, or rank support | Exact quantified change | Clicks, orders, dates | Clicks, orders, dates | Weighted metric changes | Known limitations | Direction |

Do not include sensitive credentials or account identifiers. Product identifiers may be generalized when long-term learning does not require them.

## Promotion criteria

Promote a hypothesis only when:

1. It has multiple adequately sampled intervention cycles.
2. At least three products or clearly distinct traffic contexts support it, unless the scope remains explicitly narrow.
3. Contradictory cases have been recorded and explained.
4. The mechanism is visible at a lower grain than campaign totals where possible.
5. The rule includes boundary conditions, not only a directional claim.

When evidence is mixed, mark the hypothesis Conditional and document the conditions. Never delete contradictory evidence to improve apparent consistency.
