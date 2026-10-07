


**Question:** Can you provide an example of how you used analytics tools (e.g. Excel, Tableau, Power BI, SQL) to identify an insight that influenced a business decision?

## Context

SQL has been my primary analytical tool for turning business data into actionable insight. Our clients included airline companies such as **Air Canada, WestJet, Porter, and Saudia**. Once the raw data was segmented and business rules were applied, the analysis phase began — this typically involved exploring the data, surfacing new business opportunities, and communicating findings clearly to stakeholders.

## The Business Problem

The goal was to increase **revenue margin by 10–12%** during historically weak off-season months, compared to the same period in prior years.

## My Approach (Technical)

I used a multi-step SQL query to analyze three years of performance data:

1. **First CTE** — Aggregated revenue by month and year to build a quarterly performance view for each client.
2. **Second CTE** — Applied the `RANK()` window function on top of the first CTE to rank months by revenue performance within each year, making it easy to isolate consistently low-performing periods.
3. **JOINs** — Joined the fact table (transaction-level sales data) with relevant dimension tables (date, travel agency, airline) to pull in the descriptive attributes needed for the analysis.
4. **CASE expressions** — Used to label and categorize rows (e.g., flagging months as "Off-Season" vs. "Peak-Season") for clearer reporting.

## The Insight

The ranked, multi-year view showed a consistent pattern: **June, July, and August** were reliably the lowest-performing months every year. This aligned with a known regional trend — airlines operating in the Middle East (Saudi Arabia, UAE, Qatar) tend to see a **low revenue margin (LRM)** during these summer months.

## The Business Decision It Influenced

Based on this finding, I recommended that **Saudia launch a pre-emptive off-season campaign** through their travel agency network, timed a full quarter ahead of the identified low period, rather than reacting once the dip had already started. Specifically:

- I set up **performance thresholds** for each travel agency; if an agency's bookings fell below the minimum threshold, an automated notification was triggered through Salesforce CRM, prompting the airline to work with that agency on a more targeted campaign.
- Agencies that **met or exceeded** their targets were rewarded with a monthly incentive — outside their existing SLA — which encouraged agencies to run multiple campaigns per week during the critical window.

## The Result

In 2024, Saudia's off-season revenue margin increased by **15%** year-over-year compared to the same off-season period the previous year — exceeding the original 10–12% target and directly shaping the airline's go-forward campaign strategy.

## Ideas for Extending This Analysis (worth mentioning if asked "what would you do next")

- **Forecasting:** Layer in a moving average or simple linear trend on top of the ranked historical data to predict the next off-season dip before it happens, rather than relying only on the fixed Jun–Aug pattern.
- **Cohort comparison:** Break down agency performance by tenure or region to see whether newer agencies respond differently to incentives than established ones.
- **YoY growth column:** Add a `LAG()` window function to calculate year-over-year percentage change directly in the query, rather than comparing manually across separate outputs.


