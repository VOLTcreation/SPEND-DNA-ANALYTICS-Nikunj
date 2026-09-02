# SpendDNA: Your Wallet's Year-End Story

A Python-based transaction analytics engine that decodes 6 months of messy Indian bank data into actionable spending insights, anomaly alerts, and personality archetypes.

![SpendDNA Final Report Output](Screenshot_2026-09-02_130031.png)

## Overview & Purpose

SpendDNA is an industry-grade fintech analytics tool built to mirror the daily data-cleaning and categorization work done at transaction-analytics teams at companies like Cred, Slice, and Jupiter. Taking a raw, unformatted 6-month transaction export for a synthetic persona (Rahul Sharma), this engine cleans the data, resolves hundreds of messy payment gateway abbreviations into canonical merchants, and outputs a clean, ASCII-based analytical report—often described as "Spotify Wrapped for your money".

Unlike simple expense trackers, SpendDNA tackles real-world data messiness: multi-format dates, string-based currency formats, unstructured merchant narrations, and hidden parent company names. 

## Key Technical Achievements

* **Multi-Format Date Parsing:** Built a sequential date parser to accurately handle 4 distinct and conflicting Indian bank date formats (including `DD/MM/YY` and ISO formats) without triggering common Pandas month-flipping errors.
* **100% Categorization Rate (Merchant Normalization):** Engineered a robust, pure-string vendor mapping dictionary that resolves 283 messy UPI/POS/BHIM narration strings into 39 canonical vendors. This logic dynamically handles edge cases like mapping `BUNDL Tech P L` to Swiggy, and isolates P2P transfers and ATM withdrawals.
* **Custom Z-Score Anomaly Detection:** Implemented mathematical outlier detection using Pandas `groupby` and `transform`. By calculating standard deviations strictly *within* specific categories, it surfaces genuine lifestyle anomalies (e.g., massive late-night E-commerce splurges) rather than falsely flagging standard high-ticket bills like rent.
* **Algorithmic Financial Archetyping:** Developed multi-rule algorithmic logic to assign quantitative personality archetypes based on the user's spending habits. Examples include detecting "The Shopaholic" via E-commerce spend > 15%, "The Late-Night Snacker" via time-of-day order clustering, and a custom Bengaluru-specific archetype.

## The Optimization: Eliminating the "Uncategorised" Data Leak

During initial development, the vendor mapping left 159 transactions (accounting for 10.7% of total debits) as "Uncategorised". By enhancing the mapping dictionary to capture parent company legal names (e.g., `FSN E-COMMERCE` for Nykaa) and regional transport entities (`BMTC`), the data leak was eliminated, resulting in perfectly accurate category metrics.

Here is the impact of the final vendor normalization updates:

| Metric / Section | Initial Output (Before Optimization) | Final Output (Current) |
| :--- | :--- | :--- |
| **Unique Vendors** | 32 total vendors identified. | 39 total vendors identified. |
| **"Uncategorised" Category** | Ranked 3rd overall, accounting for 10.7% (Rs. 179,944) of debits. | Completely eliminated from the Top 5 categories. |
| **"Uncategorised" Vendor** | Ranked 3rd overall, hiding 159 transactions worth Rs. 179,944. | Completely eliminated from the Top Vendors list. |
| **E-commerce Category** | Represented 35.3% of total debits (Rs. 592,816). | Increased to 36.0% of total debits (Rs. 603,877) due to newly mapped vendors. |
| **Utilities Category** | Ranked 5th at 7.8% (Rs. 130,657). | Moved up to 4th place at 8.8% (Rs. 148,182). |
| **Restaurants Category** | Not present in the Top 5 categories. | Entered the Top 5 at 5th place with 6.0% (Rs. 100,287). |
| **Flipkart Vendor Metrics** | 43 transactions totaling Rs. 170,745. | Increased to 47 transactions totaling Rs. 177,510. |
| **Swiggy Vendor Metrics** | Not present in the top 5 vendors. | Entered the top 5 vendors with 223 transactions totaling Rs. 95,523. |
| **Cafe Run Peak** | Accounted for 32.8% of cafe orders. | Increased to 35.6% of cafe orders. |
| **Top Anomalies** | Three out of four anomalies were false flags triggered by unmapped data. | Correctly identifies actual extreme spends, surfacing massive Amazon purchases. |

## The Constraints (Tech Stack)

This project was built under strict constraint discipline to demonstrate core data manipulation capabilities over automated shortcuts. 

**Allowed:**
* Python Fundamentals (functions, loops, conditionals, string methods)
* Pandas (`read_csv`, `groupby`, `pivot_table`, `.dt` accessors)
* NumPy (basic math, mean, standard deviation)

**Strictly Forbidden (Constraint Discipline):**
* **No Regular Expressions (`re`):** All 283 vendor patterns were mapped using pure Python string containment logic.
* **No Visualization Libraries (`matplotlib`, `seaborn`, `plotly`):** The final output is generated entirely through text-based ASCII formatters and f-strings.
* **No AI/ML or Profilers (`scikit-learn`, `pandas-profiling`):** All standard deviations, z-scores, and categorization logic were built natively by hand.
* **No Fintech APIs:** Zero external dependencies for transaction parsing.

## Repository Contents

* `SpendDNA_RahulSharma.ipynb`: The primary Jupyter Notebook containing the 8-feature analytics pipeline.
* `rahul_transactions.csv`: The 6-month synthetic input dataset (1,328 rows of raw bank data).
* `Screenshot_2026-09-02_130031.png`: The final terminal output report showing the 100% categorized dataset.

## How to Run

1. Clone this repository to your local machine.
2. Ensure both `SpendDNA_RahulSharma.ipynb` and `rahul_transactions.csv` are in the same directory.
3. Open the notebook via Jupyter or Google Colab.
4. Run the notebook sequentially from Cell 1 to generate the text-based terminal report.

*(Note: To run this on your own UPI/Bank data, export a 3–6 month CSV from your banking app, format the columns to match the synthetic data's headers, and update the file path in Cell 1.)*
