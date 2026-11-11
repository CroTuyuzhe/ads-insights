# Advanced Amazon Ads Operations Playbook

## Purpose and evidence status

Use this reference for architecture, scale, placement, keyword, variation, and profit planning. It synthesizes the supplied advanced advertising deck, scaling transcript, and fundamentals infographic.

Separate three layers:

- **Accounting identities:** formulas such as CPA, ACoS, and TACOS relationships.
- **Operating safeguards:** reversible changes, coverage reconciliation, exposure protection, and sample-aware decisions.
- **Course hypotheses:** auction ladders, rank mechanisms, fixed percentage thresholds, algorithm behavior, and recommended bid ratios. Test these against current account data before treating them as rules.

## 1. Start from the business role

Classify paid orders before optimizing:

- **Profit order:** `CPA < contribution profit per unit`; the ad order produces direct contribution.
- **Break-even order:** CPA is near contribution profit; judge order volume and secondary effects.
- **Investment order:** CPA exceeds unit contribution; require a defined expected return through organic rank, total sales, defensive value, or customer acquisition.

Use:

- `Ad order profit = (unit contribution before ads - CPA) x ad orders`
- `TACOS = ad spend / total sales`
- `TACOS = ACoS x ad-attributed order share` only as an approximate identity when attributed AOV and total AOV are comparable.
- `Total contribution = total sales x contribution margin before ads - ad spend`

Do not optimize investment and profit campaigns to one ACoS target. An investment campaign must state the traffic entrance, expected intervention volume, organic or total-sales indicator, time horizon, and maximum acceptable loss.

## 2. Build a qualified traffic map

Before creating ads, reconcile:

1. Own current campaigns, targets, match types, placements, search terms, negatives, and advertised ASINs.
2. Three to six strong, audience-similar competitors from multiple core queries.
3. Search volume, purchase volume or conversion proxy, competitor coverage, organic rank, paid rank, and relevance.
4. Product-page opportunities: direct competitors, substitutes, complements, category refinements, and own-ASIN defense.
5. Listing eligibility and labels: title, bullets, images, A+, Q&A, reviews, use cases, audience, function, material, and scenario.

Never call an ordered keyword or ASIN a missing opportunity merely because it is absent from one exported report. First check whether it already exists in exact, phrase, broad, auto, category, or product targeting.

### Keyword tiers

- **Upper term:** broader category concept that contains the product but also many adjacent products.
- **Core root or level-one term:** shortest phrase whose results are consistently the same product class.
- **Level-two term:** core root plus one useful attribute.
- **Level-three term:** core root plus two or more attributes.
- **Invalid attribute or material:** structurally irrelevant; candidate for phrase negative.
- **Neutral attribute:** do not pre-judge; test with bounded spend.

Competitor presence supports relevance but does not prove profitability. High variance among competitor ranks is a manual-review flag.

## 3. Model matching as coverage, not labels

Estimate:

`Eligible query set = targeting term x match rules - negative term x negative rules`

- Auto and category are broad discovery pools.
- Broad captures root combinations, order variants, plurals, and close variants; actual behavior can drift.
- Phrase preserves the core sequence while extending around it.
- Exact is a controlled query family, not always one literal string.
- Negative exact removes a narrow query family.
- Negative phrase removes that ordered phrase and extensions; use it mainly for wrong roots or intentional routing.

Use negatives for three distinct jobs:

1. **Relevance filtering:** phrase-negative demonstrably wrong materials, uses, or product types.
2. **Traffic routing:** exact-negative a harvested query in discovery after it moves to controlled exact.
3. **Budget protection:** isolate repeated high-spend, poor-economics queries after adequate evidence.

Do not over-negative discovery merely to make the report look efficient.

## 4. Design a traffic ladder

A useful architecture can move from broad discovery to controlled harvest:

`Auto/category/product expansion -> broad or phrase root -> exact query -> placement-specific exact`

The course proposes increasing effective bids with specificity. Treat the exact ratios as hypotheses. The durable principle is:

- Keep discovery bids low enough to avoid stealing controlled queries.
- Give proven exact targets enough effective bid and budget to deliver.
- Isolate high-value terms when mixed-group rotation suppresses them.
- Route harvested terms with negatives only when overlap materially harms control; duplicate eligibility cannot always be eliminated.

Choose strategy by market and budget:

- **Conversion-driven, bottom-up:** start with cheaper long-tail and discovery, harvest winners, then scale higher-volume terms. Favors fragmented traffic, competitive categories, and limited budgets.
- **Traffic-driven, top-down:** test core terms aggressively, isolate winners, and demote weak terms into broader low-bid discovery. Favors concentrated traffic, stronger budgets, and fast validation.

## 5. Scale in a controlled sequence

Before scaling a search term, require:

- Clear role: profit, investment, defense, or occupancy.
- Adequate sample and acceptable CPA or a documented investment thesis.
- Sufficient market demand.
- No proof that the organic position is already at a stable ceiling.
- Positive CTR and CVR relative to a relevant benchmark.
- Remaining TACOS or contribution-profit capacity.
- A verified customer-visible offer with no accidental price, promotion, Buy Box, or delivery failure.
- The target's own performance and bid history when the campaign contains multiple targets or auto subgroups.

Preferred scaling sequence:

1. Remove budget exhaustion if qualified traffic is being capped.
2. Check whether the target is suppressed by other targets inside the campaign.
3. Isolate it into a dedicated campaign when rotation control is valuable.
4. Add a narrower match or additional relevant targeting term.
5. Add another justified ad type or advertised ASIN.
6. Increase base bid only after estimating effective bids by placement.
7. Increase one placement selectively.

The course describes a smooth split test: launch the new isolated target with a small bid edge, observe shared delivery, pause the original, then return the new bid toward the prior effective level. Treat this as experimental because campaign history and self-competition may alter delivery.

## 6. Contract without destroying the baseline

Different levers solve different problems:

- **Budget decrease:** shortens delivery or caps clicks; it does not inherently improve traffic quality.
- **Bid decrease:** changes auction eligibility and placement distribution; it can reduce exposure nonlinearly.
- **Placement decrease:** trims one inventory source while preserving others.
- **Campaign merge:** reduces rotation opportunities without necessarily changing bid or placement.
- **Match demotion:** returns a weak exact term to a broader, lower-cost discovery pool.
- **Pause or negative:** removes eligibility; reserve for strong evidence or structural irrelevance.

Before cutting a mature campaign:

- `click capacity = proposed budget / expected CPC`
- `expected orders = click capacity x reference CVR`
- `P(zero orders) approx (1 - reference CVR) ^ click capacity`

Do not knowingly reduce a mature campaign to a sample too small to sustain its role unless volume loss is the explicit objective.

## 7. Control placements through effective bid

Collect:

- Base bid.
- Bidding strategy: fixed, down-only, up-and-down, or rule-based.
- Top of Search adjustment.
- Rest of Search adjustment where supported.
- Product Page adjustment.
- Placement impressions, clicks, CPC, CVR, CPA, ACoS, orders, and spend share.

Base placement formula:

`placement bid before dynamic adjustment = base bid x (1 + placement adjustment)`

Dynamic strategies introduce a range; do not report the placement multiplier as the final auction bid. Model the platform's documented maximum adjustment separately and label it a theoretical ceiling, not expected CPC.

Each placement is a separate auction with different inventory and purchase price. Raising the shared base bid strengthens every placement; raising one placement adjustment is more selective. A low base bid plus a large multiplier can emphasize a placement but cannot perfectly isolate it because spillover and dynamic bidding remain.

Placement actions:

- Scale a placement only if its conversion advantage can absorb the incremental CPC.
- Trim the inefficient placement multiplier before suppressing a healthy target everywhere.
- Change one placement in small steps, commonly 5-10 percentage points for mature campaigns, then evaluate on adequate clicks.
- Track spend share and order share. A placement is accretive when incremental order or contribution share exceeds its incremental spend burden.

## 8. Treat organic-rank theories as testable investment models

The course frames advertising as intervention in exposure, click, cart, purchase, expected revenue, and actual GMV signals. Use this only as a hypothesis framework:

- Paid orders may coincide with natural-rank improvement.
- Positive CTR and CVR are necessary quality signals but do not guarantee rank improvement.
- Intervention volume must be meaningful relative to keyword demand and competitive position.
- Organic ceilings can be set by offer quality, price, review strength, image, delivery, competition, and demand.
- Rank changes must be compared with price, promotion, inventory, review, listing, and competitor events.
- If rank and traffic fall after an offer failure, restore and verify the offer before using bids to force traffic. Hold advertising constant for one complete post-reset day when affordable, then scale proven traffic only after leading indicators recover.

Do not say advertising is a compliant form of rank manipulation or promise that a specific order count will create a rank. Use CPR or SPR only as rough competitive-demand estimates.

Investment test ledger:

| Field | Requirement |
|---|---|
| Target query | Search volume and current organic or paid position |
| Quality | CTR and CVR versus relevant benchmarks |
| Volume | Ad orders and total orders during intervention |
| Cost | CPA, ACoS, TACOS, and contribution loss |
| Outcome | Organic position, organic traffic, total sales |
| Confounders | Price, promotion, stock, reviews, listing, competitors |
| Stop rule | Loss ceiling or lack of rank and total-sales response |

## 9. Handle variants at the purchased-ASIN grain

For parent-child listings, distinguish:

- Advertised ASIN.
- Clicked ASIN.
- Purchased ASIN.
- Target main ASIN.
- Query-specific main variant.

A click on one variant and purchase of another should be credited to the purchased variant for product strategy, even if the ad platform attributes the order to the advertised family. Use advertised-product and purchased-product reports together.

Choose:

- **Main-variant structure:** route price, selection, creative, and ads so most purchases land on the intended main variant.
- **No-main structure:** advertise multiple variants and optimize each toward low CPA when buyer choice cannot be controlled and direct ad profitability is the priority.

Do not mix variant economics without checking which SKU received the order.

## 10. Use TACOS for portfolio decisions

Possible profit levers:

1. Keep price and TACOS stable while increasing both ad and organic orders.
2. Lower ACoS through CPC or CVR improvement so the same spend buys more orders.
3. Increase directly profitable paid orders through low-cost discovery, new ad types, audiences, or auxiliary variants.
4. Lower TACOS after natural traffic becomes stable by removing advertising that no longer creates incremental value.
5. Increase AOV or contribution margin where conversion can be protected.

Never lower TACOS by cutting ads alone without checking total orders, organic stability, and contribution profit. A lower TACOS with lower total profit is not automatically an improvement.

## 11. Course heuristics requiring validation

Treat these as starting hypotheses, never universal rules:

- CTR target around 1%.
- CVR target around 10-20% or 12-18%.
- Negating after about 20 clicks without conversion.
- Observation window of 10-20 clicks.
- Concentrating spend from 04:00-09:00.
- Keyword tier bid ladders such as exact at 160-180% of a benchmark or level-two at 120-130%.
- Raising or lowering placement adjustments until a preferred inventory mix appears.
- Competitor relevance scores of 8-10 as sufficient proof of a viable query.
- Algorithm-specific claims about A9, COSMO, Rufus, expected pit revenue, and rank response.

For each, substitute product-specific benchmarks whenever available and log supporting or contradictory evidence in `hypothesis-register.md`.

## 12. Required action output

For each proposed change, state:

- Existing campaign or target coverage.
- Role and objective.
- Current budget, base bid, bidding strategy, and placement adjustments.
- Current click capacity and expected orders.
- Current and proposed effective bid by placement.
- One primary change.
- Expected mechanism.
- Exposure floor.
- Minimum evaluation sample.
- Keep and rollback rules.
- Confidence and missing evidence.
