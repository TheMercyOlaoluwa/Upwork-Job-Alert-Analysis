# Upwork-Job-Alert-Analysis

This project analyses my personal Upwork job alerts, exported from my email. The goal was to move from an unstructured dataset (email bodies) to a structured one to uncover patterns in the job postings I receive.

The analysis answers practical questions for a freelancer:

* What time of day are most jobs posted?
* What is the busiest day of the week for new jobs?
* What is the distribution of Hourly vs. Fixed-Price jobs?
* What is the average pay rate for hourly and fixed contracts?
* What experience level (Entry, Intermediate, Expert) is most in-demand?
* Where are most clients located?
* What is the average client rating and total spend?

## Methodology

The analysis was conducted in a Python Jupyter Notebook, using the following steps:

1.  **Data Loading:** The raw `.csv` export of email alerts was loaded into a pandas DataFrame.
2.  **Data Cleaning:**
    * Irrelevant columns (like `Thread ID`) were dropped.
    * `Date Received` was converted from an object to a `datetime` type for time-series analysis.
3.  **Feature Engineering:**
    * The `Date Received` timestamp was broken down into new columns: `month_name`, `dayname`, `hour`, and `time_of_day` (Morning, Afternoon, Evening, Night).
4.  **Text Parsing (Regex):**
    * Regular expressions were used to parse the unstructured `Body` text of each email.
    * The following details were extracted into new columns:
        * `Contract Type` (Hourly or Fixed)
        * `Pay_Rate` (extracting dollar amounts)
        * `Experience_level` (Entry, Intermediate, Expert)
        * `Client_Payment_Status` (Verified or Unverified)
        * `Client_rating`
        * `Client_Spend` (parsing values like `$5K` or `$100` into numeric form)
        * `Client_Country`
5.  **Data Analysis & Visualization (EDA):**
    * Pandas was used to aggregate data and answer the key questions.
    * Matplotlib and Seaborn were used to create visualisations for trends in job frequency, pay, and client demographics.

## Key Findings

* **Best Time to Apply:** The "Night" (5:00 PM - 12:00 AM) is the most active period for new job alerts, accounting for nearly 35% of all postings.
* **Busiest Day:** Thursday is the most active day for new job alerts, followed closely by Tuesday and Wednesday. Weekends are significantly slower.
* **Pay Type:** The split is nearly 50/50 between `Hourly` (51%) and `Fixed-Price` (49%) jobs.
* **Average Pay:**
    * The average **hourly rate** offered is **$24.84/hr**.
    * The average **fixed-price** contract is **$94.14**.
* **Experience Level:** "Intermediate" (450 posts) and "Expert" (379 posts) level jobs are the most common. "Entry" level jobs are more rare (148 posts).
* **Client Location:** The United States is the dominant client country, accounting for nearly 50% of all job postings.

## Tools Used

* Python
* Pandas (for data manipulation and analysis)
* NumPy (for numerical operations)
* Matplotlib (for visualization)
* Seaborn (for visualization)
* re (for regular expressions/text parsing)
