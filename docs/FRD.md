
# Functional Requirements Document (FRD)

## Project: Agile Delivery Risk Analytics

---

## 1. System Overview

The system analyzes sprint data to:

- Measure delivery performance
- Identify inefficiencies
- Predict delivery risk
- Provide actionable insights via dashboard

---

## 2. Data Inputs

| Field               | Description                   |
| ------------------- | ----------------------------- |
| Sprint_ID           | Unique sprint identifier      |
| Planned_Work        | Total planned items           |
| Completed_In_Sprint | Items completed within sprint |
| Spillover           | Unfinished items              |
| Completion_Time     | Time taken to resolve issues  |

---

## 3. Metric Definitions

### 3.1 Commitment Reliability

Commitment_Reliability = Completed_In_Sprint / Planned_Work

---

### 3.2 Spillover Rate

Spillover_Rate = Spillover / Planned_Work

---

### 3.3 Velocity

Velocity = Total Completed_In_Sprint per sprint

---

## 4. Risk Model Logic

### 4.1 Risk Score Basis

Risk is determined using:

- Commitment Reliability
- Spillover Rate
- Data Confidence

---

### 4.2 Risk Classification

| Condition                    | Risk Level  |
| ---------------------------- | ----------- |
| Reliability < 0.5            | High Risk   |
| Reliability between 0.5–0.8 | Medium Risk |
| Reliability > 0.8            | Low Risk    |

---

### 4.3 Adjusted Risk Label

Combines:

- Risk Level
- Data Confidence

Example:

- Critical (High Confidence)
- Uncertain (Low Confidence)

---

## 5. Dashboard Components

### 5.1 Sprint Commitment vs Delivery

- Displays planned vs delivered work
- Highlights execution gap

---

### 5.2 Velocity Trend

- Shows completed work across sprints
- Identifies capacity stability

---

### 5.3 Spillover Trend

- Tracks unfinished work across sprints
- Indicates inefficiency patterns

---

### 5.4 Risk Heatmap

- Visual representation of delivery risk
- Based on commitment reliability

---

## 6. Functional Requirements

- System must calculate sprint-level metrics
- System must classify risk levels dynamically
- Dashboard must update based on input data
- Visuals must support decision-making

---

## 7. Output

- Interactive Power BI Dashboard
- Sprint-level performance insights
- Risk indicators for early decision-making

---
