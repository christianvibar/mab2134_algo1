# Data Dictionary

## Client Identifier
| Column | Type | Description |
|---|---|---|
| `client_id` | STRING | Deduplicated client identifier that groups contacts with multiple lifecycle stages into a single logical client. |
| `hubspot_client_id` | STRING | Client ID of contact in Hubspot CRM. Used as key to join with other tables. |

## Marketing Fields

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
| `lifecycle` | NUMERIC | The client's lifecycle count. Resets when a client churns or fails to convert within a 30-day window |

## Time Fields

| Column | Type | Description |
|---|---|---|
| `attributed_at` | TIMESTAMP | Timestamp of the paid attribution touch point. Distinct from `signup_at` — use carefully as a cohort anchor |
| `attributed_date` | DATE | Derived date of the `attributed_at` TIMESTAMP field |
| `signup_at` | TIMESTAMP | Date and time when the client signed up |
| `signup_date` | DATE | Derived date of the `signup_at` TIMESTAMP field |
| `customer_date` | DATE | Date when the client became a customer (reached customer lifecycle stage) |
| `first_billing_week` | DATE | First billing week when client metrics are recorded |
| `last_billing_week` | DATE | Most recent week the client was billed |

## Revenue Fields

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
| `active_weeks` | NUMERIC | Total number of weeks the client had active billing. Week count starts at 0, so a client with a complete 12-month window has active_weeks >= 51. |


## Demographic Fields

| Column | Type | Description |
|---|---|---|
| `client_country` | STRING | Client's country derived from IP address |
| `client_location_state` | STRING | Client's state/region derived from IP address |
| `client_local_timezone` | STRING | Client's local timezone derived from IP address |
| `cb_city` | STRING | Company city from Clearbit |
| `email_type` | STRING | Email classification. Values: `personal`, `business` |
| `email_industry_type` | STRING | Industry type derived from email domain. Values: `seed_brokerage_firms`, `other_brokerage_firms`, `education_services`, `other_education_services`, `NULL` |
| `cb_jobtitle_type` | STRING | Job title seniority classification. Values: `senior leadership` (C-suite, VP, Director), `non-senior leadership` |

## Firmographic Fields

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
| `revenue_first_12_months` | FLOAT | Total gross revenue in the first 12 months of the client's lifetime. Pre-computed — no aggregation needed. |
