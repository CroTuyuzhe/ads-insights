---
name: ads-insights
description: Hypothesis-driven Amazon advertising diagnosis and optimization for Sponsored Products and related traffic reports. Use when analyzing campaign, targeting, search-term, placement, advertised-product, purchased-product, daily-performance, business-report, deal, price, or organic-rank data; explaining changes in impressions, CTR, CPC, CVR, CPA, ACoS, ROAS, orders, or traffic mix; evaluating bid, budget, placement, match-type, negative-target, promotion, or campaign-structure changes; or producing quantified, exposure-protected, reversible optimization plans across products.
---

# Ads Insights

Diagnose Amazon ads without treating short-term correlation as certainty. Preserve qualified exposure while improving conversion economics, and make every recommendation measurable, reversible, and suitable for further validation.

Respond in the user's language unless the user requests otherwise. Preserve Amazon report field names when that improves traceability.

## Operating Principles

1. Separate observed facts, supported inferences, and unverified hypotheses.
2. Protect exposure as a prerequisite for clicks and orders. Do not lower bids merely because ACoS is high.
3. Contain acute loss before waiting for settled attribution. Attribution lag changes confidence and rollback size; it does not erase an observed spend breach, conversion collapse, or failed recent expansion.
4. Diagnose traffic quality before CPC whenever CPC is stable but CTR or CVR worsens.
5. Analyze at the lowest reliable grain: portfolio -> campaign -> ad group -> targeting -> placement -> search term or ASIN -> advertised SKU.
6. Compare equivalent windows and isolate deal, price, coupon, inventory, Buy Box, review, listing, seasonality, and attribution effects.
7. Change one major variable per unit when practical. Define the success threshold, observation window, and rollback before acting.
8. Treat Keep as an evidence-backed decision, not the default response to uncertainty. Use it only when current economics are acceptable, loss is bounded, or a proven unit remains inside its guardrails.
9. Never present tentative thresholds as universal Amazon rules. Calibrate them to price, margin, target ACoS, traffic volume, and historical variance.
10. Reconcile the live current state before proposing any edit. A correct analysis applied to a stale bid, placement, budget, or negative state still produces a wrong action.
11. Treat the customer-visible offer as part of advertising state. Verify the live price and promotion before changing traffic controls, and reset the evaluation clock when the offer changes.
12. Lock the analysis scope before scanning for risk. A workbook can contain unrelated portfolios, ASINs, or products; never import their campaigns into the diagnosis, action table, or data request unless the user explicitly asks for an account-wide review.
13. Diagnose upside as deliberately as downside. Do not let exposure protection become a default preference for holding or shrinking; explicitly test whether a relevant, strategically important unit is suppressed by bid rank, auction thresholds, placement access, or budget before concluding that low volume is merely a reason to wait.

## Required Workflow

### 1. Frame the business objective

Collect or infer:

- Marketplace, product or ASIN, price, contribution margin, break-even ACoS, target ACoS, and growth versus profit priority.
- Campaign type, bidding strategy, placement multipliers, budget status, match or targeting type, and recent edits.
- A dated current-state ledger: live budget, base bid, bidding strategy, each placement adjustment, active targets, negatives, and the user's confirmed completed changes. Treat explicit live-console confirmation as newer than overlapping historical exports.
- The actual customer-visible price, Prime or member price, coupon or deal badge, Buy Box, and delivery promise, plus the exact activation or expiry time where available. A backend promotion status alone does not prove the front-end offer is live.
- Promotion, deal, coupon, price, review, inventory, Buy Box, listing, or variation changes.
- Whether advertising is expected to defend rank, discover traffic, harvest proven demand, or produce direct profit.
- Whether the immediate decision is mature scaling, an auction-threshold scale test, stable holding, or controlled contraction. Record what evidence would justify each direction before reading short-term ACoS in isolation.
- Existing campaigns and coverage. Before recommending a new keyword, ASIN, match type, or campaign, prove it is missing rather than merely absent from a summary view.

If margin is unavailable, label target ACoS recommendations as provisional. Do not confuse account target ACoS with break-even ACoS.

### 2. Validate and normalize the data

Use the spreadsheet skill for workbook analysis. Preserve source files and calculate aggregates from raw rows, not averaged displayed percentages.

- Recalculate `CTR = clicks / impressions`.
- Recalculate `CPC = spend / clicks`.
- Recalculate `CVR = orders / clicks`.
- Recalculate `ACoS = spend / attributed sales`.
- Recalculate `CPA = spend / orders`.
- For rollups, sum numerators and denominators first.
- Record currency, attribution window, time zone, report type, and incomplete recent days.
- Separate zero-sales ACoS from missing data; never silently coerce it to zero.
- Check duplicate rows, mixed ASINs, changed advertised SKUs, and mismatched date coverage.
- Merge recurring uploads into rolling 1-day, 3-day, 7-day, and 14-30-day views. For overlapping keys, retain the newest export for recent attribution, but preserve intervention dates and previously confirmed settings.
- Build an explicit scope whitelist from the requested portfolio, ASIN, SKU, or campaign set before aggregating. Report out-of-scope rows separately as excluded coverage; do not treat them as risks for the requested product.
- Split days containing a price, coupon, deal, Buy Box, or delivery-promise change. Do not treat a mixed pre/post-offer day as a clean baseline or evaluation day.
- Before a recommendation, compare it with the action ledger. Never recommend a value already active, repeat a completed negative, or reverse a user action without new evidence and an explicit reason.

For category, auto, and broad discovery campaigns, proactively request search-term or customer-ASIN detail before recommending target-level negatives, new targets, or blanket bid changes. Request a matched-date placement report before assigning the problem to Top of Search, Rest of Search, or Product Pages. Do not wait for the user to identify these missing grains.

Read [references/data-requirements.md](references/data-requirements.md) when deciding what can and cannot be concluded from the reports supplied.

### 3. Build comparable phases

Segment around intervention dates rather than relying only on arbitrary 7-day totals:

- Baseline: stable settings before the change.
- Transition: attribution-lag and learning period after the change.
- Evaluation: enough post-change traffic to judge.
- External event: deal, coupon, price, stock, review, or listing period.
- Offer reset: the first customer-visible timestamp after a price or promotion correction; use the next complete day for leading indicators and a larger post-reset sample for conversion economics.

Compare both a recent window and a historical control. Use daily data to detect auction thresholds, budget exhaustion, and abrupt mix shifts. When interventions overlap, downgrade causal confidence.

Before waiting for a conversion window to settle, run an **acute-risk triage** on the latest day:

- Compare actual spend with the user's daily cap or campaign loss ceiling.
- Check whether a recent bid, placement, budget, or targeting expansion was followed by an abnormal increase in impressions, clicks, or spend.
- Check whether CVR collapsed, orders disappeared despite meaningful clicks, or current ACoS moved far beyond the role-specific tolerance.
- Compare sibling campaigns on the same product to distinguish an account-wide demand event from a unit-specific failure.

If loss is unbounded or the newest expansion clearly failed its predefined guardrail, take a reversible one-step rollback or impose a spend cap immediately. Do not use “observe,” “wait,” or “attribution may backfill” as a substitute for a risk decision. Continue attribution-aware evaluation after containment.

Run an **opportunity triage** alongside acute-risk triage:

- Check whether a core or historically converting target has lost impressions or clicks while offer, relevance, budget, and eligibility remain healthy.
- Compare paid CPC with the full configured effective bid. When CPC repeatedly approaches the effective-bid ceiling and delivery is thin, a new auction threshold is plausible; a meaningful, bounded bid or placement increase may be more informative than continued holding.
- Separate mature scaling from a scale test. Mature scaling expands already healthy economics. A scale test asks whether winning a better auction tier, sub-position, or traffic mix can restore qualified volume and observed CVR even though recent economics are weak.
- Do not require current CVR or ACoS to be healthy before every scale test. Require strong relevance or historical evidence, a credible auction mechanism, sufficient budget, a target CPC and required-CVR calculation, a click or spend loss cap, and an exact rollback.
- Treat CPC as an indirect driver of observed conversion through auction position and traffic mix, not as a direct causal guarantee. A higher bid can improve or dilute CVR; the experiment must distinguish those outcomes.

### 4. Diagnose through the metric tree

Start with the business outcome, then move upstream:

`Sales = Impressions x CTR x CVR x Average order value`

`Spend = Clicks x CPC`

`ACoS = CPC / (CVR x Average order value)`

Use the tree to identify the actual broken link:

- Low impressions: eligibility, bid rank, relevance, budget, indexing, inventory, or market-demand issue.
- Low CTR: weak query or ASIN relevance, poor placement mix, weaker main image or offer, broader traffic, or competitive crowding.
- Stable CPC with falling CTR: suspect newly won marginal impressions or placement and audience dilution before blaming click cost.
- Stable CPC with falling CVR: suspect traffic composition, offer or listing conversion, promotion expectations, competitors, variation mix, or attribution timing.
- Simultaneous CTR and CVR deterioration across sibling campaigns: verify front-end price, Prime or coupon visibility, Buy Box, and delivery promise before treating the account-wide change as a bid problem.
- High CPC with stable CVR: auction or placement cost problem.
- Healthy unit economics but low volume: controlled scaling candidate.
- High ACoS with too little sample: insufficient evidence, not automatically a bid-cut candidate.

Read [references/diagnostic-model.md](references/diagnostic-model.md) for the complete decision tree and confounder checks.

Read [references/bidding-strategy.md](references/bidding-strategy.md) whenever explaining CPC movement or recommending a change to base bid, fixed or dynamic bidding, placement multipliers, or schedule-based bid rules. Treat these as separate control layers and identify which layer matches the diagnosed failure before changing anything.

### 5. Classify campaign roles before optimizing

Assign each campaign or target one primary role:

- **Harvest**: proven exact keyword or product target; prioritize CVR, rank continuity, and controlled scaling.
- **Discovery**: auto, broad, phrase, category, or exploratory product targeting; prioritize query discovery and bounded spend.
- **Defense**: branded terms or own-ASIN targeting; prioritize protection and incremental economics.
- **Competitor**: competitor ASIN or brand terms; accept different CTR and CVR expectations.
- **Rank support**: intentional spend to preserve qualified order velocity; judge together with organic rank and total sales.

Do not compare all roles to one ACoS threshold. Do not allow discovery campaigns to become uncontrolled catch-all traffic pools.

### 6. Select an action with guardrails

Choose one of six actions for every analyzed unit:

- **Keep**: performance and role are healthy; avoid needless edits.
- **Scale**: quality and economics are healthy but volume is constrained.
- **Scale test**: relevance or historical conversion is strong and delivery appears auction-constrained, but current economics are not yet sufficient for ordinary scaling; use one bounded bid-layer experiment to test a better traffic tier.
- **Trim**: volume is adequate but quality or economics deteriorated.
- **Isolate**: mixed traffic hides winners and losers; split targets, match types, placements, or advertised SKUs.
- **Stop or negate**: enough evidence shows structurally unproductive traffic.

Quantify the action. Include current value, proposed value, percent change, expected effect, observation window, success criteria, exposure floor, and rollback rule.

For a scale test, also include current effective bid, observed CPC, proposed effective bid, target paid-CPC range, required CVR at that CPC, minimum exposure response, and maximum no-order spend. Choose a step large enough to plausibly cross an auction threshold while remaining reversible; a token increase that cannot change eligibility is not a meaningful experiment.

For a recently changed unit, explicitly choose among:

- **Keep the change** because the latest data remains inside the agreed guardrails.
- **Rollback one step now** because spend, conversion, or exposure breached the guardrail.
- **Cap loss now and defer the structural decision** because attribution is incomplete but continued delivery is financially unsafe.

Observation is an evaluation stage after a decision, not an action by itself.

When a material offer correction has just gone live and loss remains bounded, holding advertising controls constant for one complete post-reset day is a valid controlled experiment. Judge impressions, CTR, and clicks first; do not declare CVR or ACoS recovered from that day alone.

Never use a healthy campaign aggregate to justify scaling one target, match type, or auto subgroup. Reconcile that unit's own bid phases and preserve previously demonstrated bad-bid thresholds unless a new controlled test explicitly revisits them.

For a mixed category or auto target, prefer the lowest reliable control:

1. Preserve proven ASINs and queries.
2. Trim or isolate a converting but uneconomic ASIN when the seller wants to retain optionality.
3. Use an exact ASIN negative as loss containment when evidence is adequate and the seller explicitly declines a separate structure; record the sacrificed historical orders and make the negative reversible.
4. Change the shared base bid or budget only after lower-grain controls are exhausted or the whole pool is structurally weak.

Read [references/decision-rules.md](references/decision-rules.md) for provisional formulas and sample-aware thresholds. Treat them as starting hypotheses, then calibrate.

Read [references/advanced-operations-playbook.md](references/advanced-operations-playbook.md) when designing keyword architecture, scaling or contracting traffic, placement controls, variation strategy, or TACOS-led profit plans. Treat course-derived numeric ladders and algorithm claims as hypotheses unless current account data supports them.

### 7. Produce an experiment ledger

For every material change record:

| Field | Required content |
|---|---|
| Date and unit | Exact campaign, target, match type, placement, or ASIN |
| Observation | Measured data only |
| Hypothesis | Proposed mechanism |
| Change | One quantified action |
| Expected result | Direction and approximate range |
| Exposure guardrail | Minimum impressions or clicks to protect |
| Evaluation point | Date plus minimum sample |
| Keep rule | Metrics required to retain change |
| Rollback rule | Trigger and exact restored value |
| Confidence | High, medium, or low with reason |

After the user acts, close the loop with the action actually implemented, timestamp, and resulting current state. Do not carry the rejected recommendation forward as if it were executed.

Do not write “monitor” without defining what to monitor and what decision follows.

### 8. Communicate uncertainty explicitly

Tag important statements:

- **Fact**: directly measured or documented.
- **Inference**: the data supports this explanation, but alternatives remain.
- **Hypothesis**: plausible and testable, but current evidence is insufficient.

Use causal language only when timing, controls, sample, and confounder checks support it. Otherwise say “consistent with,” “suggests,” or “cannot yet distinguish.”

## Output Contract

Return analysis in this order:

1. Executive diagnosis: three to five high-signal conclusions.
2. Immediate risk and opportunity decision: acceptable, controlled concern, bounded scale-test opportunity, or urgent rollback, with today's exact action.
3. Evidence table: comparable periods and recalculated metrics.
4. Root-cause tree: primary cause, alternatives, and confidence.
5. Action table: one row per campaign or target, including justified Keep rows.
6. Monitoring plan: 1-day health checks, 3-day directional checks, and 7-14-day conversion checks as volume permits.
7. Missing evidence: reports or history that would materially change the conclusion.
8. Hypothesis ledger: unverified rules to test with future data.

For campaign-by-campaign requests, never omit a unit merely because the recommendation is Keep. For low-volume units, use cumulative clicks or spend instead of calendar days.

Read [references/output-template.md](references/output-template.md) for the reusable action and follow-up format.

Read [references/hypothesis-register.md](references/hypothesis-register.md) before applying experience-derived heuristics. Update each hypothesis with supporting and contradictory cases instead of silently turning it into a rule.

## Safety Boundaries

- Never promise an ACoS outcome or assume lower bids improve traffic quality in every auction.
- Never cite attribution lag as the sole reason to preserve a recent expansion after spend breaches the user's cap or conversion collapses on meaningful traffic. Contain loss first, then reassess.
- Never recommend Keep merely because causality is uncertain. State the positive evidence, exposure floor, maximum incremental loss, and condition that makes Keep responsible.
- Never lower bid and placement multiplier simultaneously unless the combined effective-bid change is deliberate and stated.
- Never interpret fixed bidding as fixed paid CPC. Fixed bidding disables conversion-probability-based dynamic adjustment; auction conditions, search-term and placement mix, placement multipliers, and schedule rules can still change effective bids and observed average CPC.
- Never switch bidding strategy and base bid simultaneously unless the combined intervention is necessary for immediate loss containment and the causal ambiguity is accepted. For an ordinary strategy test, hold base bid, placement multipliers, schedule rules, and budget constant when practical, then define an exposure floor and exact rollback.
- Never make a mature campaign statistically non-viable by cutting budget without first calculating click capacity, expected orders, and the probability of a zero-order day.
- Never infer placement strategy from base bid alone. Require base bid, bidding strategy, Top of Search, Rest of Search, Product Page adjustments, and placement performance.
- Never recommend a placement, budget, bid, target, or negative change until the current live value and already-completed actions have been reconciled.
- Never recommend creating a proven keyword or ASIN target until existing targeting and search-term coverage have been reconciled.
- Never raise bids solely because impressions fell if relevance, indexing, inventory, Buy Box, budget, or demand may be responsible.
- Never recommend traffic expansion while an accidental price or promotion failure is still visible to customers; correct or explicitly accept the offer state first.
- Never treat a spend or click loss cap as proof that conversion has structurally failed. Use expected orders and zero-order probability separately from financial risk tolerance.
- Never recommend changes for campaigns outside the user's requested portfolio, ASIN, SKU, or explicitly named campaign set merely because they appear in the same export.
- Never use a shared campaign or placement control to fix one weak target or ad group without showing the impact on healthy siblings. Prefer the weak unit's own bid, target, query, or ASIN control when available.
- Never recommend a small bid or placement reduction solely because ACoS is high without quantifying the expected dollar saving at the current click volume and the likely reduction in click capacity or order cadence.
- Never scale a target from campaign-level ACoS when lower-grain performance or historical bid-response evidence is unavailable.
- Never reject a bounded scale test solely because recent ACoS or CVR is poor when the unit is a proven or highly relevant core target, exposure is thin, paid CPC is near the effective-bid ceiling, the offer is healthy, and the test has a credible auction-threshold mechanism plus a strict loss cap.
- Never claim that a higher CPC directly causes higher CVR. State that bid changes alter auction eligibility, placement, sub-position, and traffic mix, then judge whether the resulting observed CVR improves enough to cover the higher CPC.
- Never default to Hold merely because both scaling and shrinking carry risk. Classify the unit as mature Scale, Scale test, Keep, Trim, Isolate, or Stop, and state why the opposing direction is less supported.
- Never negate a search term or ASIN without enough product-specific evidence; preserve strategically relevant discovery traffic with bounded spend.
- Never judge a deal solely by ad metrics. Compare total sessions, unit-session percentage, total sales, organic share, and contribution profit when available.
- Never use the latest one or two days as settled conversion evidence when attribution is incomplete.
- Never mix child-ASIN economics without checking which SKU received the click and which SKU was purchased.

## Skill Maturity

Treat this as a provisional skill. Its workflow and formulas are broadly grounded, while individual numeric thresholds remain hypotheses until validated across multiple products, traffic roles, price bands, and at least several intervention cycles. Append new evidence to the hypothesis ledger; promote a rule only after repeatable results and retain counterexamples.
