# MAB2134 - Analytics Algorithms 1 Project

## Project Title: Predicting Customer Lifetime Value to Guide Paid Advertising Budget Allocation

### Stakeholders
Marketing team responsible for paid advertising strategy and budget planning.

### Business Problem
The current Customer Lifetime Value (CLV) model relies on manually-maintained retention curves with a shifting denominator, making it unreliable for comparing customer value across channels and segments. This leads to the risk of persistently misallocating paid advertising budget toward lower-value segments, compounding into lower marketing ROI over time.

### Decision / Action
Allocate paid advertising budget toward acquisition channels and segments that predict higher 12-month customer lifetime value. Outputs also inform algorithmic bidding on platform auctions.

### Unit of Analysis
One customer (one row = one customer record).

### Target / Structure
**Phase 1:** Unsupervised. Discover natural customer segments from behavioral data; validate whether manual customer segment labels correspond to meaningfully distinct groups.
**Phase 2:** Supervised. Predict 12-month gross revenue per customer in absolute dollars (observed; take rate applied post-model at the decision layer).

### Prediction Horizon
At or near customer acquisition. Before any retention, upsell, or account management action is taken.

### Data Source
Internal company data warehouse (production gold layer), 2022–2024 customer cohorts. PII scrubbed prior to use.
Features: acquisition channel, service offering, TQL status, plan/tier, starting assistant count, transaction frequency.
Row count to be confirmed upon data pull.

### Success Metric
TBD

### Expected Business Value
A defensible, data-driven basis for paid advertising budget allocation that reduces the risk of chronic misallocation toward low-value customer segments.

### Risks
Missing data: low to medium. Will use gold layer data from company dataset. Will have to double check if all relevant variables are still updated.
Leakage: to be audited in EDA; features must be observable at acquisition time only.
Ethics: low. Internal B2B data, PII scrubbed, outputs used for budget decisions not individual client actions.
Feasibility: clustering might not find new segments. Regression model might not predict well if key drivers of customer value are not captured in the available features.

### Important Files
[Data Dictionary](https://github.com/christianvibar/mab2134_algo1/blob/75681427885c9a45c28ab401efaec1bff4c9b289/data_dictionary.md)
