# A/B Testing Analysis: Marketing Campaign Performance

Which of two ad campaigns was the better use of budget? This project compares a **Control** and a **Test** campaign over 30 days of ad data, using Python, and ends with a budget recommendation.

## Question

Both campaigns drove a similar number of purchases. Did the Test campaign's different setup actually pay off, or is the Control campaign still the more cost-efficient choice?

## Dataset

- `control_group.csv` and `test_group.csv`: one row per day for 30 days (Aug 2019), 60 rows in total
- Columns: spend (USD), impressions, reach, website clicks, searches, view content, add to cart, purchases
- Days with missing values were excluded from the totals below

## Method

1. Load, clean and merge the two campaign files
2. Exploratory analysis of each funnel stage (impressions to clicks to add-to-cart to purchase)
3. Compare purchases, conversion rates and cost per purchase
4. Check whether the daily purchase difference is statistically meaningful
5. Visualise the results and write a recommendation

## Results

| Metric | Control | Test |
|---|---|---|
| Total spend (USD) | 66,818 | 76,892 |
| Total purchases | 15,161 | 15,637 |
| **Cost per purchase (USD)** | **4.41** | **4.92** |
| Click-through rate (clicks / impressions) | 4.86% | 8.09% |
| Purchases per website click | 9.83% | 8.64% |
| Add-to-cart to purchase | 40.2% | 59.1% |
| Average purchases per day | 522.8 | 521.2 |

- **Purchases per day are statistically the same.** Welch t-statistic on daily purchases is about 0.03, so there is no evidence either campaign sells more.
- **The Test campaign attracted more clicks and converted more add-to-carts, but it cost more per purchase** (USD 4.92 vs 4.41, about 12% higher).
- Higher spend did not buy more purchases, so cost per purchase is the deciding metric here.

## Recommendation

- Keep the **Control campaign** as the default because it is more cost-efficient for the same purchase volume.
- Investigate why the Test campaign earns more clicks and add-to-cart conversions before dropping it, since its engagement is clearly stronger.
- Track cost per purchase alongside conversion rate in future A/B tests, and run each test long enough to confirm significance.

## Limitations

- Only 30 days per campaign, so the sample is small.
- Spend was not equal across the two campaigns, which makes a like-for-like comparison harder.

## Tools

Python, pandas, matplotlib, Google Colab. Notebook: `AB_Testing_Analysis.ipynb`.
