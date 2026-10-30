---
marp: true
theme: default
paginate: true
---

# ai04: SQL for Machine Learning

**Applications of Artificial Intelligence**
Medina County Career Center | Ryan McMaster, CTE Instructor

---

## Why SQL in an AI Course?

**The Reality of Real-World ML:**
- Most data doesn't come from CSV files
- Companies store billions of records in databases
- **SQL lets you filter BEFORE loading** (saves memory!)
- **SQL lets you combine data sources** (essential for features)
- **SQL lets you create aggregations** (crucial for ML features)

**Today:** Learn to connect to a database and extract data efficiently

---

## What You're Learning

**SQL Basics (04a):**
- Connect to SQLite database with Python
- SELECT, FROM, WHERE, ORDER BY, LIMIT
- Filter data with WHERE conditions
- Sort results with ORDER BY

**Aggregation (04b):**
- GROUP BY (summarize by categories)
- COUNT, SUM, AVG, MIN, MAX
- HAVING (filter groups)
- JOINs (combine tables)

---

## Our Dataset: NBA Basketball Stats

**5 Seasons of Real Data:**
- 30 NBA teams
- Hundreds of players
- 4,000+ games per season
- Detailed game statistics

**Tables in the Database:**
- `teams` — Team info (name, city, founded year)
- `players` — Player names and IDs
- `team_game_stats` — One row per game per team
- `player_season_stats` — One row per player per season

---

## SQL Query Structure

```sql
SELECT   column1, column2     -- WHAT to show
FROM     table_name          -- WHERE to get it
WHERE    condition           -- FILTER rows
ORDER BY column              -- SORT results
LIMIT    10                  -- HOW MANY rows
```

**Order matters!** Always use this sequence.

---

## Example: Find Top Scorers

**Question:** "What players averaged 20+ points per game in 2021-22?"

```sql
SELECT player_id, pts, gp
FROM player_season_stats
WHERE season = '2021-22' AND pts >= 20 AND gp >= 40
ORDER BY pts DESC
LIMIT 10
```

**Result:** DataFrame with top 10 scorers

---

## The Python Workflow

```python
import pandas as pd
import sqlite3

# 1. Connect
conn = sqlite3.connect('nba_5seasons.db')

# 2. Write query
query = """
SELECT full_name, pts, ast
FROM player_season_stats
WHERE season = '2021-22' AND pts >= 20
ORDER BY pts DESC
"""

# 3. Execute and load
df = pd.read_sql(query, conn)

# 4. Use for ML
print(df)
```

---

## Common SQL Operators

| Operator | Meaning | Example |
|----------|---------|----------|
| `=` | Equal | `WHERE state = 'Ohio'` |
| `!=` | Not equal | `WHERE state != 'Texas'` |
| `>`, `<` | Greater/less than | `WHERE pts > 20` |
| `>=`, `<=` | Greater/less or equal | `WHERE gp >= 40` |
| `BETWEEN` | In range | `WHERE pts BETWEEN 15 AND 25` |
| `AND`, `OR` | Combine conditions | `WHERE pts > 20 AND gp >= 40` |

---

## This Week's Tasks

**04a: SQL Basics**
- Write SELECT queries on NBA data
- Filter with WHERE
- Sort with ORDER BY
- Control results with LIMIT

**04b: Aggregation**
- COUNT players per team
- AVG points per season
- SUM rebounds by group
- HAVING to filter groups

**DIY Task:** Discover 5 interesting stats from NBA data

---

## Let's Code!

**Open:** `ai04_Walkthrough.ipynb`

Start with Part 1: Database Connection

Questions? Check the **SQL_Quick_Reference_ai04a.md** guide!

---
