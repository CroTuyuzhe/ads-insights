# Diagnostic Model

## Contents

1. Metric identities
2. Decision tree
3. Traffic structure
4. Confounder checks
5. Confidence scoring

## 1. Metric identities

Use weighted calculations:

- `CTR = clicks / impressions`
- `CPC = spend / clicks`
- `CVR = orders / clicks`
- `AOV = sales / orders`
- `CPA = spend / orders`
- `ACoS = spend / sales`
- `ROAS = sales / spend`
- `ACoS = CPC / (CVR x AOV)` when units are consistent
- `Maximum CPC at target ACoS = AOV x CVR x target ACoS`
- `Break-even CPC = AOV x CVR x break-even ACoS`
- `Required CVR = CPC / (AOV x target ACoS)`
- `Orders = impressions x CTR x CVR`
- `Sales = impressions x CTR x CVR x AOV`
- `Revenue per click = CVR x AOV`
- If only AOV changes and all else is equal, the maximum proportional CVR decline that preserves revenue per click is `1 - old AOV / new AOV`.

Use rates as decimals in formulas. These identities diagnose arithmetic pressure, not causality.

## 2. Decision tree

### Impressions declined

Check in order:

1. Inventory, Buy Box, listing status, indexing, and category eligibility.
2. Market demand and keyword rank.
3. Daily budget exhaustion or campaign status.
4. Bid and effective placement bid changes.
5. Relevance and historical conversion signals.

If impressions and clicks both fall after a bid reduction but CTR and CVR remain healthy, restore only enough bid to regain the exposure floor. If impressions fall while relevance or demand also fell, raising bids may buy worse traffic.

### Impressions rose, CTR fell

Likely mechanisms:

- Newly won low-relevance auctions.
- Mix shifted from exact or close match toward substitutes, complements, broad queries, categories, or product pages.
- Placement mix expanded into lower-attention inventory.
- Competitor offer or creative improved.
- Main image or offer became less compelling relative to the auction set.

If CPC is stable, the problem can still be material because click volume and conversion quality depend on which impressions were won.

### CTR stable, CVR fell

Check:

- Search-term or ASIN composition beneath the aggregate.
- Price, coupon, deal, shipping promise, Buy Box, rating, review count, and listing changes.
- Child-ASIN mix and purchased-product mix.
- Competitor price and promotion.
- Attribution lag or abnormal day-of-week traffic.

### CPC rose, CTR and CVR stable

Auction cost or placement inflation is the leading explanation. Calculate the maximum sustainable CPC from target ACoS. Trim base bid or the inefficient placement multiplier while protecting order-producing exposure.

### CPC stable, CTR and CVR fell

Treat traffic-quality dilution as the leading hypothesis. Stable CPC does not mean stable traffic. Compare search terms, product targets, placements, and match mix before cutting all bids.

### ACoS worsened with little sample

Do not optimize on the ratio alone. Use click, spend, and expected-order thresholds. One missed conversion can dominate low-volume ACoS.

### Price or promotion changed

Treat the customer-visible offer as an upstream traffic variable, not only an AOV input:

- A higher final price can improve revenue per order while reducing CTR and CVR by more than the AOV gain can absorb.
- Expiry of a Prime, member, coupon, or deal price can remove both the lower price and its visible badge, affecting search-page clicks as well as detail-page conversion.
- Compare revenue per click before and after the offer change. If CVR falls by more than `1 - old AOV / new AOV`, the higher order value cannot preserve the prior sales yield even before considering CTR loss.
- Verify both front-end price presentation and backend promotion status. Record the exact visible start or expiry time and exclude the mixed day from clean phase comparisons.
- When the offer is corrected, hold ads constant for one complete post-reset day if financial risk is bounded. Use that day for impressions, CTR, and click direction; require adequate clicks and attribution time for CVR and ACoS.

## 3. Traffic structure

Measure, when available:

- Paid versus organic session or traffic share.
- Branded versus generic demand.
- Exact or harvested versus discovery spend.
- Search placements versus product-page placements.
- Core high-intent terms versus long-tail or adjacent terms.
- Own-ASIN, competitor-ASIN, category, substitute, and complement traffic.
- New-to-brand or repeat demand where applicable.

A healthy structure is product-specific, but generally has:

- A protected conversion core that generates repeatable orders.
- Bounded discovery that produces new harvestable terms or targets.
- Separate defense and competitor economics.
- No single broad or auto pool consuming uncontrolled spend.
- Enough qualified traffic to support rank without making the product dependent on weak paid traffic.

## 4. Confounder checks

Before attributing a result to an ad change, check:

- Deal or coupon start and end.
- Actual customer-visible final price, Prime or member price, and badge visibility versus backend-only status.
- Exact offer activation or expiry time and whether a reporting day mixes two prices.
- Rating or review changes.
- Inventory, delivery promise, and Buy Box.
- Main image, title, A+, variation, or suppressed-content changes.
- Competitor price, promotion, stock, or review movement.
- Search demand, seasonality, weekday, and event traffic.
- Simultaneous base-bid, placement, budget, targeting, and listing edits.
- Attribution lag and late-reported orders.

Promotions can increase traffic volume while lowering aggregate CTR or CVR if the promotion broadens audience reach or attracts price-sensitive browsing. Never assume a deal must improve both metrics.

## 5. Confidence scoring

### High confidence

- Adequate sample in both periods.
- One dominant intervention with a clear date.
- Equivalent weekday and promotion conditions.
- Target or search-term level evidence supports the aggregate movement.
- Alternative causes were checked.

### Medium confidence

- Direction is repeated and material, but one or two confounders remain.
- Sample is adequate at campaign level but weak at lower grain.

### Low confidence

- Fewer than expected clicks or orders.
- Multiple overlapping edits.
- Missing change history or promotion context.
- Conclusion relies on one or two days.
- Only aggregate campaign data is available.

State confidence beside the cause, not in a distant disclaimer.
