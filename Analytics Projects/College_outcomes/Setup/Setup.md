# Data Setup Instructions

This guide describes how to load the **college outcomes dataset** into a local Postgres database for analysis.

---

## Prerequisites
- PostgreSQL installed and running locally
- `csvkit` installed (`pip install csvkit`)
- Database created (e.g., `analytics`)

```bash
createdb analytics

1. Normalize the CSV header (lowercase only)

Lowercase only the header row to avoid quoted identifiers in Postgres.

awk 'NR==1{print tolower($0); next}1' \
  ~/Documents/Python/Analytics/college2008sub.csv \
  > ~/Documents/Python/Analytics/college2008sub_clean.csv

  2.Generate a Postgres DDL file

Infer column types and create a SQL schema from the CSV.
csvsql \
  --dialect postgresql \
  --tables college_sub \
  --snifflimit 100000 \
  ~/Documents/Python/Analytics/college2008sub_clean.csv \
  > create_college_sub.sql

  sed 's/"//g' create_college_sub.sql > create_college_sub_clean.sql

3. Create the table

Run the DDL in Postgres:
psql analytics -f create_college_sub_clean.sql

4. Load the data

Use \copy so Postgres reads the CSV from your machine:

psql analytics -c "\copy college_sub FROM '/Users/sonal/Documents/Python/Analytics/college2008sub_clean.csv' CSV HEADER"

5. Sanity checks

Run quick validations to confirm data load:

-- row count
SELECT COUNT(*) FROM college_sub;

-- sample peek
SELECT * FROM college_sub LIMIT 5;

-- check null counts for a key column
SELECT COUNT(*) FILTER (WHERE median_earnings IS NULL) AS null_median_earnings
FROM college_sub;