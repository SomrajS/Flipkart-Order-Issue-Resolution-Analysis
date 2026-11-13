[README.md](https://github.com/user-attachments/files/34784289/README.md)
# Flipkart Order Issue Resolution & Customer Support Analytics

## Project Overview

This project analyzes order, refund, and customer complaint records to help a support operations team investigate order-related issues and prioritize cases that may need attention.

The project was completed as part of a structured course assignment. The original Jupyter notebook is preserved with its engineering handover brief, milestone instructions, implementation work, and automated assessment section.

The deliverable is an analysis workflow and operational handover report—not a web application or dashboard.

## Project Objectives

- Inspect the order, refund, and customer complaint source files.
- Clean and standardize records while preserving legitimate multiple refund and complaint records.
- Analyze order status, product-category revenue, delivery delays, refund outcomes, and complaint patterns.
- Combine the cleaned information into a one-row-per-order investigation dataset.
- Apply transparent, rule-based support priorities.
- Export detailed order-level and priority-summary reports.

## Tools & Technologies

- Python
- Pandas
- Jupyter Notebook / Google Colab
- CSV, Excel (`.xlsx`), and JSON data files

## Input Data

The notebook expects the following three source files, with their original filenames:

| File | Purpose |
|---|---|
| `orders.csv` | Order details, customer information, order status, amounts, and delivery dates |
| `refunds.xlsx` | Refund request records and refund outcomes |
| `customer_complaints.json` | Customer complaint records, categories, and statuses |

**Data note:** The course instructions say not to submit the original input datasets unless specifically requested. Do not publish customer or otherwise confidential information. If you want to provide sample data, use a sanitized or synthetic version and make that clear.

## Project Workflow — 10 Milestones

1. **Establish the order baseline** — Load and inspect the orders data, including record counts, distinct IDs, data types, and missing values.
2. **Onboard finance and customer support data** — Load and inspect refund and complaint sources, including outcome and complaint-category summaries.
3. **Prepare reliable order records** — Deduplicate orders, standardize statuses, convert amounts and dates, and create `orders_clean`.
4. **Make issue records consistent** — Clean refund and complaint records, resolve duplicate issue IDs, standardize fields, and create `refunds_clean` and `complaints_clean`.
5. **Measure delivery reliability** — Analyze order status and category revenue, calculate delivery delay in days, and compare delayed orders across cities.
6. **Connect refunds to original orders** — Summarize refund counts, total refund amounts, and pending or failed refunds at order level.
7. **Find repeat complaint patterns** — Analyze complaint categories and statuses, repeated complaints by order, and repeat contacts by customer.
8. **Deliver one order investigation view** — Join cleaned orders with refund and complaint summaries while retaining orders with no associated issues; validate the one-row-per-order result.
9. **Prepare a support triage queue** — Create traceable issue flags and assign support priorities using the rules below.
10. **Hand over the operational report** — Produce a detailed priority-sorted report, a priority summary, and exported CSV and Excel files.

## Support Priority Rules

The notebook uses transparent business rules rather than a predictive model. It evaluates three signals:

- A delivered order is more than **3 days late**.
- The order has at least one **pending or failed refund**.
- The order has **more than one complaint**.

Priority is assigned based on the number of signals:

| Priority | Rule |
|---|---|
| High | Two or more signals apply |
| Medium | Exactly one signal applies |
| Low | No signals apply |

Delivered orders with incomplete delivery-date information are flagged separately for review rather than automatically being treated as on time.

## Outputs

After the notebook has been run successfully, it creates:

| Output | Description |
|---|---|
| `final_orders_df` | Consolidated one-row-per-order working dataset |
| `final_report` | Detailed order-level report sorted from High to Low priority |
| `priority_summary` | Count of orders in each support-priority category |
| `flipkart_order_issue_report.csv` | Exported detailed order issue report |
| `flipkart_issue_summary.xlsx` | Exported support-priority summary |

The notebook also includes a final automated assessment/self-check section. The course brief describes this as a formative check, not a secure examination or a substitute for human review.

## How to Run

### Option 1: Google Colab

1. Open the notebook in Google Colab.
2. Make your own copy using **File → Save a copy in Drive**.
3. Run the setup cell and provide the three required input files.
4. Run the notebook cells in order, from the beginning through all ten milestones.
5. Review the outputs and complete the written handover findings using values from your actual analysis.
6. Run the automated assessment only after running all preceding cells.
7. Download or retain the generated CSV and Excel reports as needed.

### Option 2: Jupyter Notebook

1. Install Python and Jupyter Notebook.
2. Install the required packages:

   ```bash
   pip install pandas openpyxl jupyter
   ```

3. Place the notebook and the three input files in the same working directory.
4. Start Jupyter Notebook and open the `.ipynb` file.
5. Run all cells in order.

The notebook checks for the input files in its working directory. In Google Colab, it can prompt for file uploads when the files are missing.

## Notes & Limitations

- Results depend on the supplied input datasets and the cleaning decisions documented in the notebook.
- The README does not state numerical findings because those should be copied from the actual outputs produced by running the completed notebook.
- The support-priority classification is a rule-based triage aid, not a prediction of customer behavior or a guarantee of issue severity.
- The automated assessment is described in the course brief as a formative self-check. A fresh-kernel run and human review of calculations, data-quality decisions, and written findings remain important.

## Course Assignment Disclosure

This repository contains work completed as part of a course assignment. The original notebook retains the provided project brief, milestone-by-milestone instructions, and assessment guidance. The notebook is shared for learning and portfolio demonstration.

## Author

**Somraj Sarkar**
