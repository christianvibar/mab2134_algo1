# MAB2134 - Analytics Algorithms 1 Project

## Project Title: Predicting Customer Lifetime Value to Optimize Value-Based Bidding and Paid Advertising Budget Allocation

### Stakeholders
Marketing team responsible for paid advertising strategy and budget planning.

### Business Problem
The current Customer Lifetime Value (CLV) model relies on manually-maintained retention curves with a shifting denominator, making it unreliable for comparing customer value across channels and segments. This leads to the risk of persistently misallocating paid advertising budget toward lower-value segments, and undermines the effectiveness of value-based bidding (VBB) — an algorithmic bidding strategy that requires accurate customer value signals to optimize bids on ad platform auctions. Without a reliable CLV estimate, both manual budget allocation and automated bidding decisions are built on a flawed foundation, compounding into lower marketing ROI over time.

### Decision / Action
Allocate paid advertising budget toward acquisition channels and segments that predict higher 12-month customer lifetime value. Model outputs also serve as the customer value signal for value-based bidding (VBB) on paid ad platform auctions, enabling the platform's algorithm to automatically optimize bids toward higher-value customer acquisition.

### Unit of Analysis
One customer (one row = one customer record).

### Target / Structure
Predict 12-month gross revenue per customer in absolute dollars at or near acquisition time. The modeling approach and algorithm selection will be informed by EDA findings.

### Prediction Horizon
At or near customer acquisition. Before any retention, upsell, or account management action is taken.

### Data Source
Internal company data warehouse (production gold layer), 2022–2024 customer cohorts. PII scrubbed prior to use.
Features: acquisition channel, service offering, TQL status, plan/tier, starting assistant count, transaction frequency.
Row count to be confirmed upon data pull.

### Success Metric
TBD. Success metric will be informed by the modeling approach selected by EDA findings.

### Expected Business Value
A defensible, data-driven basis for paid advertising budget allocation that reduces the risk of chronic misallocation toward low-value customer segments.

### Risks
Missing data: low to medium. Will use gold layer data from company dataset. Will have to double check if all relevant variables are still updated.
Leakage: to be audited in EDA; features must be observable at acquisition time only.
Ethics: low. Internal B2B data, PII scrubbed, outputs used for budget decisions not individual client actions.
Feasibility: clustering might not find new segments. Regression model might not predict well if key drivers of customer value are not captured in the available features.

### Important Files
- [Data Dictionary](https://github.com/christianvibar/mab2134_algo1/blob/75681427885c9a45c28ab401efaec1bff4c9b289/data_dictionary.md)
- [Notebooks](https://github.com/christianvibar/mab2134_algo1/tree/75681427885c9a45c28ab401efaec1bff4c9b289/notebooks)
- [Data](https://github.com/christianvibar/mab2134_algo1/tree/a4532ee010e846f46f3d163d3cf461d77241112d/data)
