# Data Requirements

## Purpose

Use the strongest available report set while stating the limits of each grain. More files do not automatically create causal proof; aligned dates and identifiable intervention points matter more.

## Minimum viable inputs

For a directional diagnosis, request:

- Campaign report with date, campaign, impressions, clicks, spend, sales, and orders.
- Exact change log with date, old value, new value, and reason.
- Current-state snapshot from the live console: budget, base bid, bidding strategy, placement adjustments, active targets, and negatives.
- Customer-visible list price, final price, Prime or member price, coupon or deal badge, and target ACoS or margin context. Record the exact visible activation or expiry time when known.

This supports campaign-level trends but cannot reliably identify bad search terms, ASINs, or placements.

## Preferred diagnostic stack

| Report | Main use | Important limits |
|---|---|---|
| Campaign daily detail | Phase changes, budgets, trend breaks | Mix can hide target-level shifts |
| Targeting daily detail | Bid-response and match or target quality | Does not reveal each customer query |
| Search-term report | Query relevance, harvesting, negatives | Recent conversions may lag |
| Placement report | Top, rest-of-search, product-page economics | Placement multipliers and base bid interact |
| Advertised-product report | SKU-level traffic and economics | Variation traffic may purchase another SKU |
| Purchased-product report | Halo and cross-SKU conversion | Attribution is not organic incrementality |
| Business report | Sessions, unit-session percentage, total sales | Different traffic and attribution definitions |
| Organic rank or traffic words | Paid-organic structure and rank support | Rank movements have multiple causes |
| Change history | Intervention segmentation | Missing edits sharply lower causal confidence |
| Current-state and action ledger | Prevent stale or duplicate recommendations | Historical report fields may lag or repeat old settings |
| Deal, price, coupon, inventory log | External-event controls | Badge visibility and actual price must be verified |
| Front-end offer snapshot | Confirms visible price, Prime or member treatment, coupon, Buy Box, and delivery promise | Backend status can disagree or update at a different time |

## Data quality checks

0. Define the requested scope as a whitelist of portfolios, ASINs, SKUs, or campaigns before calculating totals. Count and disclose excluded out-of-scope rows, but do not analyze or request detail for them unless the user expands the scope.
1. Confirm the report time zone and marketplace.
2. Confirm the attribution window and whether recent days are incomplete.
3. Confirm currency and tax treatment.
4. Confirm that rows do not mix products with materially different prices or margins.
5. Confirm whether budgets ran out and at what time.
6. Confirm Buy Box, inventory, suppression, and indexing status.
7. Confirm whether a bid value is base bid or effective bid after placement adjustments.
8. Confirm bidding strategy: fixed, dynamic down only, or up and down.
9. Recalculate ratios from sums; never average daily CTR, CVR, CPC, or ACoS.
10. Mark zero-sales rows distinctly from missing sales.
11. Reconcile every proposed value against the newest user-confirmed live setting and completed-action ledger.
12. When daily exports overlap, deduplicate by the lowest available business key plus date and keep the newest export for attributed performance. Never overwrite the separately maintained setting-change history.
13. Verify the customer-facing offer independently of backend configuration and mark any day that contains an offer transition.
14. For a mixed campaign, do not apply campaign-level economics to a target or subgroup without its own daily targeting or search-term evidence and bid history.

## Evidence limits by data availability

- Campaign-only data: recommend campaign controls, but label target or search-term causes as hypotheses.
- Targeting data without search terms: detect target deterioration, but do not claim which query caused it.
- Search-term data without placements: diagnose relevance, but avoid attributing the problem to top-of-search versus product pages.
- Placement data without bid history: describe placement performance, but do not claim an exact bid caused the change.
- Advertising data without business reports: assess attributed performance, but do not claim total-profit or organic-rank impact.
- Short window under roughly one conversion cycle: use leading indicators and defer final CVR or ACoS decisions.
- Offer correction without a complete post-change day: assess front-end state and leading delivery only; do not recommend simultaneous traffic expansion unless loss or rank risk explicitly outweighs causal clarity.

## Window design

Prefer:

- 1-day checks for delivery failures, budget exhaustion, extreme CPC, or broken exposure.
- 3-day checks for directional changes when daily clicks are sufficient.
- 7-day checks for normal-volume conversion and ACoS.
- 14-30-day checks for sparse targets, seasonality, or rank effects.

Replace calendar windows with sample thresholds when volume is low. Always compare the same weekdays when day-of-week effects are meaningful.

For category, auto, and broad campaigns, request 7 days of search-term detail for normal-volume units and 14-30 days for sparse or volatile units. If the user supplies recurring daily files, combine them into these rolling windows rather than analyzing each upload in isolation.
