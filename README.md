##**SpendDNA: Your Wallet's Year-End Story**##

A Python-based transaction analytics engine that decodes 6 months of messy Indian bank data into actionable spending insights, anomaly alerts, and personality archetypes.

***The Project***
SpendDNA is a fintech analytics tool built to mirror the daily data-cleaning and categorization work done at companies like Cred, Slice, and Jupiter. Taking a raw, unformatted 6-month transaction export for a synthetic persona (Rahul Sharma), this engine cleans the data, resolves hundreds of messy payment gateway abbreviations into canonical merchants, and outputs a clean, ASCII-based analytical report—often described as "Spotify Wrapped for your money."

Key Achievements:

100% Categorization Rate: Engineered a robust, pure-string vendor mapping dictionary that resolved 283 messy UPI/POS/BHIM narration strings into 39 canonical vendors, successfully dropping the "Uncategorised" data leak to zero.

Multi-Format Date Parsing: Built a sequential date parser to accurately handle 4 distinct and conflicting Indian bank date formats without ISO month-flipping errors.

Custom Z-Score Anomaly Detection: Implemented mathematical outlier detection within Pandas groupby parameters to surface genuine lifestyle anomalies (e.g., massive late-night E-commerce splurges) rather than standard high-ticket bills like rent.

Financial Archetyping: Developed multi-rule algorithmic logic to assign quantitative personality archetypes. (e.g., detecting "The Shopaholic" via E-commerce spend > 15%, and "The YOLO Spender" via negative savings rates).

The Constraints (Tech Stack)
This project was built under strict constraint discipline to demonstrate core data manipulation capabilities over automated shortcuts.

Allowed:

Python Fundamentals (functions, loops, conditionals, string methods)

Pandas (read_csv, groupby, pivot_table, .dt accessors)

NumPy (basic math, mean, standard deviation)

Strictly Forbidden:

No Regular Expressions (re): All 283 vendor patterns were mapped using pure Python string containment logic.

No Visualization Libraries (matplotlib, seaborn, plotly): The final output is generated entirely through text-based ASCII f-string formatting.

No AI/ML or Profilers (scikit-learn, pandas-profiling): All standard deviations, z-scores, and categorization logic were built by hand.

No Fintech APIs: Zero external dependencies for transaction parsing.

Repository Contents
SpendDNA_RahulSharma.ipynb: The primary Jupyter Notebook containing the 8-feature analytics pipeline.

rahul_transactions.csv: The 6-month synthetic input dataset (1,328 rows of raw bank data).

Screenshot_2026-09-02_130031.png: The final terminal output report.

How to Run
Clone this repository to your local machine.

Ensure both SpendDNA_RahulSharma.ipynb and rahul_transactions.csv are in the same directory.

Open the notebook via Jupyter or Google Colab.

Run the notebook sequentially from Cell 1 to generate the terminal report.
