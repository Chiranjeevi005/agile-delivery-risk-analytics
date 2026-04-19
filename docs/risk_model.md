# Risk Model Documentation

## Methodology
The risk model is an early warning system designed to predict sprint delivery risk using mid-sprint progress signals. It evaluates actual work started against expected progress at two checkpoints (Day 3 and Day 7) of a 14-day sprint. Progress is evaluated using ratio-based normalization to account for varying sprint commitments.

## Formulas
* **Expected_Completion_Day3**: `Planned_Work * (3 / 14)`
* **Expected_Completion_Day7**: `Planned_Work * (7 / 14)`
* **Actual_Progress_Day3**: Sum of `Work_Started_Flag` where `Created_Date <= Sprint_Start_Date + 3`
* **Actual_Progress_Day7**: Sum of `Work_Started_Flag` where `Created_Date <= Sprint_Start_Date + 7`
* **Risk_Score**: `(Expected_Progress / Actual_Progress)` (If `Actual_Progress = 0`, score is 999)
* **Predicted_Risk**:
  * High Risk: `Risk_Score > 1.5`
  * Medium Risk: `Risk_Score > 1.2`
  * Low Risk: `Risk_Score <= 1.2`

## Assumptions
* Sprints follow a uniform 14-day schedule.
* Work effort should be roughly linear throughout the sprint.
* Starting work late in the sprint is a primary indicator of delivery risk.

## Limitations
* Does not account for varying complexity of individual tasks.
* Weekends and holidays within the 14-day sprint window are treated the same as workdays.
* Relies on accurate `Created_Date` and `Sprint_Start_Date` synchronization.

## Validation Results
* Predictions were cross-referenced against the `Actual_Risk` classification (Critical/Moderate/Low).
* Model successfully flags high-risk sprints early, with ratios normalizing across small vs. large sprints.

## Insights
* **Early activity highly correlates with final delivery**: Sprints that build momentum by Day 3 consistently hit >85% completion.
* **Low early progress indicates failure**: A delay in generating initial pull requests or advancing Jira tickets rapidly escalates the probability of sprint spillover (Risk Score > 1.5).
