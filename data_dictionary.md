# Data Dictionary

## Marketing Fields (STRING)

| Column | Type | Description | Source Model(s) |
|---|---|---|---|
| `broader_source` | STRING | High-level acquisition source grouping. Values: `paid_inbound`, `organic_inbound`, `outbound`, `referral` | `dim_clients`, `fct_client_multi_lifecycles` |
| `broad_source` | STRING | Granular acquisition source. Values: `adwords`, `facebook`, `organic_seo`, `direct`, `partner_referral` | `dim_clients`, `fct_client_multi_lifecycles` |
| `channel` | STRING | Marketing channel at acquisition. Values: `adwords`, `facebook`, `bing`, `linkedin`, `reddit`, `organic`, `direct` | `dim_clients`, `fct_client_multi_lifecycles` |
| `service_offering` | STRING | Service the client was interested in based on the ad/page they saw. Values: `executive_assistant`, `virtual_assistant`, `bookkeeper` | `dim_clients`, `fct_client_multi_lifecycles` |
| `campaign_group` | STRING | Campaign group classification at acquisition | `fct_client_multi_lifecycles` |
| `campaign` | STRING | Campaign name at acquisition | `dim_clients`, `fct_client_multi_lifecycles` |
| `ad_group` | STRING | Ad group name at acquisition | `dim_clients`, `fct_client_multi_lifecycles` |
| `ad` | STRING | Ad name at acquisition | `dim_clients`, `fct_client_multi_lifecycles` |
| `ad_network` | STRING | Ad network at acquisition. Values: `FB`, `Google Ads`, `LinkedIn`, `Bing` | `dim_clients`, `fct_combined_ad_network_stats`, campaign stats models |
| `creative_group` | STRING | Creative group classification at acquisition | `dim_clients`, `fct_client_multi_lifecycles` |
| `creative_variation` | STRING | Creative variation at acquisition | `dim_clients`, `fct_client_multi_lifecycles` |
| `keyword_text` | STRING | Keyword text from the acquisition search ad | `fct_client_multi_lifecycles` |
| `keyword_match_type` | STRING | Keyword match type at acquisition. Values: `EXACT`, `PHRASE`, `BROAD` | `dim_clients`, `fct_client_multi_lifecycles` |
| `placement` | STRING | Ad placement at acquisition (e.g. `facebook_ads_on_reels`) | `dim_clients`, `fct_client_multi_lifecycles` |
| `facebook_ad_set_audience` | STRING | Facebook ad set audience at acquisition | `fct_client_multi_lifecycles` |

## Time Fields (DATE/TIMESTAMP)

| Column | Type | Description | Source Model(s) |
|---|---|---|---|
| `attributed_at` | TIMESTAMP | Timestamp of the paid attribution touch point. Distinct from `signup_at` — use carefully as a cohort anchor | `dim_clients`, `fct_client_multi_lifecycles` |
| `signup_at` | TIMESTAMP | Timestamp when the client signed up | `fct_client_multi_lifecycles`, `fct_signups` |
| `signup_date` | DATE | Date when the client signed up. Key field for cohort analysis and lifecycle window boundaries | `fct_client_multi_lifecycles`, `fct_signups` |
| `customer_date` | DATE | Date when the client became a customer (reached customer lifecycle stage) | `dim_clients_multi_lcs` |
| `week` | DATE | Finance week ending date (Friday–Thursday week structure) | Various marketing/finance models |
| `first_week` | DATE | First billing week when client metrics are recorded | `dim_clients` |

## Revenue Fields (INTEGER/NUMERIC)

| Column | Type | Description | Source Model(s) |
|---|---|---|---|
| `total_revenue` | NUMERIC | Total lifetime revenue from this client across all deals and weeks | `dim_clients` |
| `revenue_first_1_month` | NUMERIC | Total revenue in the client's first 1 month | `dim_clients` |
| `revenue_first_2_months` | NUMERIC | Total revenue in the client's first 2 months | `dim_clients` |
| `revenue_first_3_months` | NUMERIC | Total revenue in the client's first 3 months | `dim_clients` |
| `revenue_first_6_months` | NUMERIC | Total revenue in the client's first 6 months | `dim_clients` |
| `revenue_first_12_months` | NUMERIC | Total revenue in the client's first 12 months | `dim_clients` |
| `starting_mrr` | NUMERIC | MRR from the client's first billing week (excludes zero values) | `fct_client_multi_lifecycles` |
| `latest_mrr` | NUMERIC | MRR from the client's most recent billing week | `dim_clients`, `fct_client_multi_lifecycles` |
| `profit` | NUMERIC | Total lifetime profit (revenue minus costs) | `dim_clients` |
| `wrr` | NUMERIC | Weekly recurring revenue. Converts to MRR via `wrr * 4.33` | `dim_clients`, finance models |
| `mrr` | NUMERIC | Monthly recurring revenue. Often calculated as `wrr * 4.33`. Sum of MRR across all deals sharing the same latest charge day | `dim_clients`, multiple finance/lifecycle models |

## Demographic Fields (STRING)

| Column | Type | Description | Source Model(s) |
|---|---|---|---|
| `client_country` | STRING | Client's country derived from IP address | `dim_clients` |
| `client_location_state` | STRING | Client's state/region derived from IP address | `dim_clients` |
| `client_local_timezone` | STRING | Client's local timezone derived from IP address | `dim_clients` |
| `cb_city` | STRING | Company city from Clearbit | `dim_clients` |
| `email_type` | STRING | Email classification. Values: `personal`, `business` | `dim_clients` |
| `email_industry_type` | STRING | Industry type derived from email domain. Values: `seed_brokerage_firms`, `other_brokerage_firms`, `education_services`, `other_education_services`, `NULL` | `dim_clients` |
| `cb_jobtitle` | STRING | Client's job title from Clearbit | `dim_clients` |
| `cb_jobtitle_type` | STRING | Job title seniority classification. Values: `senior leadership` (C-suite, VP, Director), `non-senior leadership` | `dim_clients` |

## Firmographic Fields (STRING)

| Column | Type | Description | Source Model(s) |
|---|---|---|---|
| `cb_employees_range` | STRING | Company employee count range from Clearbit (e.g. `11-50`, `51-250`) | `dim_clients` |
| `cb_annual_revenue_ranges` | STRING | Company annual revenue range from Clearbit (e.g. `$1M-$10M`) | `dim_clients` |
| `cb_industry` | STRING | Company industry from Clearbit (e.g. `Real Estate`, `Technology`) | `dim_clients` |
| `cb_sector` | STRING | Company sector from Clearbit — higher level than industry | `dim_clients` |
| `cb_industry_group` | STRING | Industry group from Clearbit — between sector and industry in granularity | `dim_clients` |
| `cb_sub_industry` | STRING | Sub-industry from Clearbit — more specific than industry | `dim_clients` |

---

## Target Variable

| Column | Type | Definition |
|---|---|---|
| `revenue_first_12_months` | FLOAT | Total gross revenue in the first 12 months of the client's lifetime. Pre-computed — no aggregation needed. Take rate (51%) applied post-model at the decision layer. |
