# Data Dictionary

## Processed Dataset: `sprint_dataset.csv`

| Field Name | Description | Source | Transformation Logic |
| :--- | :--- | :--- | :--- |
| `Issue_ID` | Unique identifier for the issue | Apache / GitHub | Extracted from raw issue number/key |
| `Created_Date` | Timestamp of issue creation | Apache / GitHub | Synchronized to 2024 timeline |
| `Resolved_Date` | Timestamp of issue resolution/closure | Apache / GitHub | ISO Format; NULL if open |
| `Source` | Original platform of the record | Metadata | Literal string: "GitHub" or "Apache" |
| `Standardized_Status`| Harmonized status category | Derived | Mapped to: **To Do**, **In Progress**, **Done** |
| `Assignee` | User identifier assigned to the work | Apache / GitHub | Direct extraction; "Unassigned" if empty |
| `Milestone` | Release or project grouping | Apache / GitHub | Direct extraction from meta-data |
| `Sprint_ID` | Global time-based sprint identifier| Derived | Unified 14-day intervals |
| `Sprint_Start_Date` | Start date of the assigned sprint | Derived | ISO Format: `YYYY-MM-DD 00:00:00` |
| `Sprint_End_Date` | End date of the assigned sprint | Derived | ISO Format: `YYYY-MM-DD 23:59:59` |
| `Completion_Time`| Total days to resolve | Derived | `Resolved_Date - Created_Date` in decimal days |
| `Issue_Type` | Categorized work type | Derived | Extracted from keywords |
| `Completion_Flag` | Numeric binary for finished work | Derived | 1 if Done, 0 otherwise |
| `Data_Quality_Flag` | Record integrity status | Derived | "Valid" or "Review" |
| `Issue_Age` | Days since creation | Derived | `Today - Created_Date` |
| `Planned_Flag` | Work committed to the sprint | Derived | **1** if `Created_Date <= Sprint_End_Date` for its assigned bucket |
| `Completed_In_Sprint_Flag`| Successful delivery within window | Derived | **1** if `Resolved_Date <= Sprint_End_Date` and Status is **Done** |
| `Carry_Forward_Flag`| Post-sprint completion indicator | Derived | **1** if `Status == Done` but `Resolved_Date > Sprint_End_Date` |

## Limitations & Assumptions
* **Sprint Identification**: Sprints are simulated using fixed 14-day intervals from the global project start. This may not reflect actual Jira sprint boundaries.
* **Planning Simulation**: The `Planned_Flag` assumes all items created within a sprint window are part of that sprint's commitment.
* **Commitment Data**: The dataset lacks explicit "Committed" vs "Added-after-start" markers from Jira history (Audit logs); these are simulated via time-windows.
