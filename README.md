# Analytics
# SQL Analytics Portfolio

This repository contains my SQL-based analytics projects and case studies.  
Each folder/project demonstrates **end-to-end SQL problem solving** — from dataset exploration, modeling, and query design to business insights.  

---

## 📂 Structure

```text
sql-analytics/
│
├── README.md                  # This file
├── projects/                  # Individual analytics projects
│   ├── colleges_outcomes/     
│   │   ├── queries.sql        # Core SQL queries
│   │   ├── notes.md           # Assumptions, design decisions, tradeoffs
│   │   └── results.md         # Final findings / business insights
│   └── <next_project_name>/
│       ├── queries.sql
│       ├── notes.md
│       └── results.md
└── utils/                     # (Optional) Common snippets/functions

Current Projects

1. Colleges Outcomes Analysis
	•	Goal: Explore how college graduates perform financially after graduation, analyzing median earnings and debt-to-income ratios.
	•	Dataset: US Dept of Education College Scorecard dataset.
	•	Highlights:
	•	Calculated median salaries across majors and institutions.
	•	Analyzed debt ratios vs. post-grad income levels.
	•	Built queries to bucket graduates into salary tiers.

👉 See colleges_outcomes/queries.sql

⸻

🔮 Upcoming Ideas
	•	Subscription churn analysis (predictive SQL features).
	•	Experimentation data stratification (user-level vs. geo-level randomization).
	•	E-commerce funnel drop-off metrics.

⸻

🛠️ Tech & Tools
	•	SQL (Presto, Hive, Snowflake, BigQuery)
	•	dbt for modeling (optional integration)
	•	Visualization in Tableau/Looker (outside SQL repo)

⸻

✍️ Author

Sonal Sharma — Data Engineer & Analytics Consultant