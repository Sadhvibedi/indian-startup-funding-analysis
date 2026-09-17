# Indian Startup Funding Analysis

Analysis of Indian startup funding data (2015–2020) to identify funding
patterns across sectors, cities, investors, investment types, and time,
using Python, pandas, and SQL.

## Project Objective

- Identify the most funded startup sectors
- Find major startup funding cities
- Identify top investors by number of funding deals
- Analyze funding trends over time
- Identify popular investment types
- Find the most highly funded startups

## Dataset

Source: [Indian Startup Funding — Kaggle](https://www.kaggle.com/datasets/sudalairajkumar/indian-startup-funding)

~3,000 funding records covering Indian startups from 2015 to 2020, including
startup name, industry, city, investors, investment type, and funding amount.

## Data Cleaning

The raw data had several quality issues that were fixed before analysis:

- **Dates** were stored in inconsistent formats (e.g. `22/01//2015`,
  `05/072018`) — parsed using a regex-based date extractor instead of a
  single fixed format, to avoid silently losing rows.
- **Funding amounts** were stored as text with commas, `N/A`, and
  `Undisclosed` values — cleaned and converted to numbers, with missing
  amounts kept as `NaN` rather than filled with zero.
- **City and industry names** had multiple spellings for the same value
  (e.g. `Bangalore` vs `Bengaluru`, `eCommerce` vs `E-Commerce`) —
  standardized using mapping dictionaries.
- **Investor names** were stored as comma-separated lists in a single
  column — split and expanded into individual investor records for
  accurate investor-level analysis.

## Key Findings

- The dataset holds 3,044 funding records covering 2,452 unique startups,
  but only 67.9% disclose an amount. All totals represent disclosed
  funding, not true market size.
- The median deal is $1,750,000 against a mean of $18,445,630 — a handful
  of mega-rounds pull the average well above what a typical startup raises.
- E-Commerce leads on capital raised, with $8,961M (23.5% of all disclosed
  funding), while Consumer Internet records the most deals (941).
- Funding is geographically concentrated: Bengaluru, Mumbai and Gurugram
  together account for 71.7% of disclosed funding.
- Sequoia Capital is the most active investor with 72 deals, ahead of
  Accel Partners (68).
- Seed Funding is the most common deal structure (1,362 deals), consistent
  with an early-stage-heavy market.
- Flipkart raised the most overall ($4,760M across 6 disclosed rounds).
- Capital peaked in [YEAR] ($[AMOUNT]M) while deal count peaked in [YEAR]
  ([NUMBER] deals).

## Tools Used

Python · pandas · NumPy · matplotlib · seaborn · SQLite (SQL)

## How to Run

1. Download the dataset from Kaggle and place `startup_funding.csv` in the
   same folder as the notebook.
2. Open `Indian_Startup_Funding_Analysis.ipynb` in Jupyter or Google Colab.
3. Run all cells from top to bottom.

## Limitations

- A portion of funding amounts are undisclosed, so totals reflect disclosed
  funding only, not the true market size.
- When multiple investors are listed for one deal, the full amount is
  attributed to each investor, so investor totals should not be summed.
- Industry and city classifications depend on the original dataset's
  categorization.
