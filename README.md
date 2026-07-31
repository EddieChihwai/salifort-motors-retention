# Salifort Motors: Employee Retention Prediction

## Business Problem
Salifort Motors is experiencing an unacceptably high rate of employee turnover. Turnover incurs heavy costs in recruitment, training, and lost productivity. The executive team requires a data-driven model to predict which employees are at the highest risk of leaving and to identify the underlying structural causes of this attrition.

## Data & Methodology
This project analyzed 14,999 employee records, assessing variables such as self-reported satisfaction, average monthly hours, project load, and tenure.

The workflow followed the PACE framework (Plan, Analyze, Construct, Execute):
*   **Data Cleaning & EDA:** Removed duplicates and handled tenure outliers. EDA revealed non-linear relationships between workload metrics and turnover.
*   **Baseline Model:** Trained a Logistic Regression classifier, which achieved only a 19% recall for departing employees. This confirmed that the drivers of turnover were complex and non-linear.
*   **Champion Model:** Engineered, trained, and tuned a Random Forest Classifier to accurately map feature interactions without assuming linearity.

## Results
The optimized Random Forest model achieved a **92% recall** in identifying employees who left the company, meaning it successfully flagged 92% of the actual flight risks. Overall model accuracy reached 99%.

Feature importance extraction revealed that turnover is primarily driven by operational mechanics rather than compensation or department:
1.  **Workload Extremes:** `number_project` and `average_monthly_hours` were top predictors. Employees are leaving due to extreme over-utilization (burnout) or severe under-utilization.
2.  **Tenure Stagnation:** `time_spend_company` proved to be a major factor, with a significant spike in turnover around the 4-year mark.
3.  **Satisfaction:** `satisfaction_level` acts as a strong trailing indicator, heavily influenced by the workload issues above.

## Business Recommendations
*   **Implement Project Caps:** Institute a strict upper limit on concurrent projects assigned to individual employees to prevent systematic burnout.
*   **Audit 4-Year Promotion Paths:** HR must systematically intervene at the 3.5 to 4-year tenure mark to outline pathways for promotion, lateral movement, or upskilling.
*   **Monitor Overtime:** Establish automated HR check-ins for employees consistently logging over 200 hours per month.

## Repository Structure
*   `/data`: Contains raw and processed datasets (Note: raw HR data is ignored in version control for privacy/security best practices).
*   `/notebooks`: Contains the primary Jupyter notebook detailing the end-to-end data pipeline, model training, and evaluation.
*   `/reports`: Contains the final executive summary.