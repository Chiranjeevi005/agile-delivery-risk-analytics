# Sprint Predictability & Risk Analytics Dashboard

## Dashboard Purpose
The Sprint Dashboard serves as an executive-level interactive decision tool. It visualizes Agile delivery performance, highlights actual vs. planned delivery metrics, and incorporates predictive risk models to flag sprint failure early. This tool empowers engineering leaders to make data-driven interventions and adjust operational cadences mid-sprint.

## Metrics Definition
* **Commitment Reliability**: Ratio of items successfully delivered within the sprint vs. total items committed at sprint planning.
* **Spillover Rate**: Percentage of work deferred or carried over to the next print.
* **High Risk Count**: Total count of sprints flagged as 'High Risk' via early Day-3 / Day-7 momentum checkpoints.
* **Prediction Accuracy**: The aggregate percentage metric denoting how often the mid-sprint predictive risk aligned precisely with the empirical end-of-sprint outcome.

## Usage Instructions
1. **Executive Overview (Page 1):** Review top-level KPIs (Commitment, Spillover, Risk Count). This page serves as a fast status check for the portfolio.
2. **Risk Prediction (Page 2):** Use to monitor active mid-sprints. Specifically focus on the Risk Heatmap and distributions to validate where interventions are needed before Day 14.
3. **Drill-down Analytics (Page 3):** Utilize the `Issue_Type` and `Source` (GitHub vs Apache Jira) filters to segment performance root causes globally or regionally.

*Source File Required:* `sprint_dashboard.pbix`
*Underlying Dataset:* `excel-model/sprint_analysis.xlsx`
