# 🛢️ Global Oil Spill Incident Analysis

## Overview
SQL-based analysis of pipeline oil spill incidents reported to NOAA, focusing on incident trends, operator risk rankings, anomaly detection, and geographic hotspots across the United States.

## Tools & Platform
- **SQL** (BigQuery)
- **Dataset:** NOAA Oil Spill Incidents
- **Rows:** ~85 aggregated monthly records | 19 columns

## Key Questions Answered
- Which months and years saw the highest incident spikes?
- Which pipeline operators carry the most risk (incidents, costs, barrels lost)?
- Which U.S. states are the highest-risk zones?
- Are there statistically significant anomalies in incident trends?

## SQL Techniques Used
| Technique | Purpose |
|---|---|
| `WITH` / CTEs | Multi-stage data pipeline (clean → aggregate → rank → detect) |
| `PARSE_DATETIME` | Standardizing raw datetime strings |
| `EXTRACT(YEAR/MONTH)` | Time-based aggregation |
| `AVG() / STDDEV() OVER()` | Statistical anomaly detection |
| `DENSE_RANK() OVER()` | Operator & state risk ranking |
| `CASE WHEN` | Spike classification (SPIKE DETECTED / NORMAL) |
| Rolling 12-month window | Trend smoothing |

## CTE Pipeline
```
clean_table → monthly_incidents → yearly_growth → spike_detection → operator_risk → state_risk → final_output
```

## Key Findings
- Anomaly detection flagged periods where yearly incidents exceeded **1.5× standard deviation** above the historical mean
- **Enterprise Crude Pipeline LLC** ranked as the highest-risk operator by total incidents and costs
- **Texas** consistently ranked as the #1 highest-risk state for pipeline spills

## Files
| File | Description |
|---|---|
| `global_oil_spill.csv` | Aggregated monthly incident data with risk rankings |
| `screenshots/` | BigQuery SQL query screenshots |

## Data Source
[NOAA Oil Spill Incidents](https://www.noaa.gov/) — accessed via BigQuery public dataset

---
*Project by Stephanie Sambo | Data Analyst | Oil & Gas | SQL • BigQuery*
