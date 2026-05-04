# Data Dictionary

## Variable Candidate List

| Column | Type | Definition |
|---|---|---|
| `channel` | STRING | Marketing channel from max paid attribution. Values: `adwords`, `bing`, `facebook`, `organic`, `direct`. |
| `broader_source` | STRING | High-level source grouping. Values: `paid_inbound`, `organic_inbound`, `outbound`, `referral`. |
| `service_offering` | STRING | Service the client was looking for based on the ad/page they saw (e.g. `executive_assistant`, `virtual_assistant`). |
| `is_sales_tql` | BOOL | TRUE if client is a Team Qualified Lead (TQL). Combines Clearbit, Dreamdata, and manual enrichment. Primary TQL flag. |
| `tql_category` | STRING | Detailed TQL classification: Gold Standard TQL, Platinum TQL, and several non-TQL tiers based on enrichment source and qualification. |
| `initial_plan_type` | STRING | Plan type of client's first deal (e.g. `full_time`, `part_time`). |
| `max_initial_default_hours` | FLOAT | Maximum default hours among client's initial deals. Proxy for starting assistant count. |
| `max_initial_price_point` | STRING | Maximum price point among client's initial deals (e.g. `10/hr`, `14/hr`). |
| `first_week_mrr` | FLOAT | Monthly recurring revenue in the client's first billing week. |
| `company_industry` | STRING | Industry classification from HubSpot. ~40% missing — treat nulls as separate category or drop. To be decided in EDA. |

### Target Variable

| Column | Type | Definition |
|---|---|---|
| `revenue_first_12_months` | FLOAT | Total gross revenue in the first 12 months of the client's lifetime. Pre-computed — no aggregation needed. Take rate (51%) applied post-model at the decision layer. |
