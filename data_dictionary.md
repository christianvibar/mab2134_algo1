# Data Dictionary

## Marketing Fields (STRING)

| Column | Type | Description |
|---|---|---|
| `broader_source` | STRING | High-level acquisition source grouping. Values: `paid_inbound`, `organic_inbound`, `outbound`, `referral` |
| `broad_source` | STRING | Granular acquisition source. Values: `adwords`, `facebook`, `organic_seo`, `direct`, `partner_referral` |
| `channel` | STRING | Marketing channel at acquisition. Values: `adwords`, `facebook`, `bing`, `linkedin`, `reddit`, `organic`, `direct` |
| `service_offering` | STRING | Service the client was interested in based on the ad/page they saw. Values: `executive_assistant`, `virtual_assistant`, `bookkeeper` |
| `campaign_group` | STRING | Campaign group classification at acquisition |
| `campaign` | STRING | Campaign name at acquisition |
| `ad_group` | STRING | Ad group name at acquisition |
| `ad` | STRING | Ad name at acquisition |
| `ad_network` | STRING | Ad network at acquisition. Values: `FB`, `Google Ads`, `LinkedIn`, `Bing` |
| `creative_group` | STRING | Creative group classification at acquisition |
| `creative_variation` | STRING | Creative variation at acquisition |
| `keyword_text` | STRING | Keyword text from the acquisition search ad |
| `keyword_match_type` | STRING | Keyword match type at acquisition. Values: `EXACT`, `PHRASE`, `BROAD` |
| `placement` | STRING | Ad placement at acquisition (e.g. `facebook_ads_on_reels`) |
| `facebook_ad_set_audience` | STRING | Facebook ad set audience at acquisition |

## Time Fields (DATE/TIMESTAMP)

| Column | Type | Description |
|---|---|---|
| `attributed_at` | TIMESTAMP | Timestamp of the paid attribution touch point. Distinct from `signup_at` — use carefully as a cohort anchor |
| `signup_date` | DATE | Date when the client signed up. Key field for cohort analysis and lifecycle window boundaries |
| `customer_date` | DATE | Date when the client became a customer (reached customer lifecycle stage) |
| `first_billing_week` | DATE | First billing week when client metrics are recorded |
| `last_billing_week` | DATE | Most recent week the client was billed |

## Revenue Fields (INTEGER/NUMERIC)

| Column | Type | Description |
|---|---|---|
| `total_revenue` | NUMERIC | Total lifetime revenue from this client across all deals and weeks |
| `revenue_first_1_month` | NUMERIC | Total revenue in the client's first 1 month |
| `revenue_first_2_months` | NUMERIC | Total revenue in the client's first 2 months |
| `revenue_first_3_months` | NUMERIC | Total revenue in the client's first 3 months |
| `revenue_first_6_months` | NUMERIC | Total revenue in the client's first 6 months |
| `revenue_first_12_months` | NUMERIC | Total revenue in the client's first 12 months |
| `starting_mrr` | NUMERIC | MRR from the client's first billing week (excludes zero values) |
| `latest_mrr` | NUMERIC | MRR from the client's most recent billing week |
| `profit` | NUMERIC | Total lifetime profit (revenue minus costs) |
| `wrr` | NUMERIC | Weekly recurring revenue. Converts to MRR via `wrr * 4.33` |
| `mrr` | NUMERIC | Monthly recurring revenue. Often calculated as `wrr * 4.33`. Sum of MRR across all deals sharing the same latest charge day |

## Demographic Fields (STRING)

| Column | Type | Description |
|---|---|---|
| `client_country` | STRING | Client's country derived from IP address |
| `client_location_state` | STRING | Client's state/region derived from IP address |
| `client_local_timezone` | STRING | Client's local timezone derived from IP address |
| `cb_city` | STRING | Company city from Clearbit |
| `email_type` | STRING | Email classification. Values: `personal`, `business` |
| `email_industry_type` | STRING | Industry type derived from email domain. Values: `seed_brokerage_firms`, `other_brokerage_firms`, `education_services`, `other_education_services`, `NULL` |
| `cb_jobtitle` | STRING | Client's job title from Clearbit |
| `cb_jobtitle_type` | STRING | Job title seniority classification. Values: `senior leadership` (C-suite, VP, Director), `non-senior leadership` |

## Firmographic Fields (STRING)

| Column | Type | Description |
|---|---|---|
| `cb_employees_range` | STRING | Company employee count range from Clearbit (e.g. `11-50`, `51-250`) |
| `cb_annual_revenue_ranges` | STRING | Company annual revenue range from Clearbit (e.g. `$1M-$10M`) |
| `cb_industry` | STRING | Company industry from Clearbit (e.g. `Real Estate`, `Technology`) |
| `cb_sector` | STRING | Company sector from Clearbit — higher level than industry |
| `cb_industry_group` | STRING | Industry group from Clearbit — between sector and industry in granularity |
| `cb_sub_industry` | STRING | Sub-industry from Clearbit — more specific than industry |

---

## Target Variable

| Column | Type | Definition |
|---|---|---|
| `revenue_first_12_months` | FLOAT | Total gross revenue in the first 12 months of the client's lifetime. Pre-computed — no aggregation needed. Take rate (51%) applied post-model at the decision layer. |
