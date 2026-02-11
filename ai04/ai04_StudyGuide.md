# ai04 SQL for Machine Learning — Study Guide

**Applications of Artificial Intelligence**
Medina County Career Center | Ryan McMaster, CTE Instructor

---

## Vocabulary & Key Terms (15-20 terms)

### Core SQL Concepts

**SQL (Structured Query Language)**
- Language for asking questions of databases
- Used by 99% of companies with large data systems
- Example: "Show me all players who scored 25+ points"

**Query**
- A question you ask the database
- Written in SQL syntax
- Returns a result set (rows and columns)

**Database**
- Organized collection of related data
- Stores millions or billions of records
- Accessed through SQL queries

**SQLite**
- Lightweight, file-based database system
- Entire database stored in a single `.db` file
- No server needed (unlike MySQL, PostgreSQL)
- Perfect for learning and small applications

**Table**
- Organized collection of related records
- Like a spreadsheet with rows and columns
- Example: `teams` table has 30 rows (one per NBA team)

**Row**
- Single record in a table
- Example: One row = one team's info

**Column**
- Attribute or field in a table
- Example: `full_name`, `state`, `year_founded` are columns in `teams` table

**Index**
- Database tool that speeds up queries
- Like a book's index — helps you find data faster

---

### SELECT & FROM

**SELECT**
- Specifies which columns to display
- `SELECT full_name, pts` — show only these two columns
- `SELECT *` — show all columns

**FROM**
- Specifies which table to query
- `FROM teams` — get data from the teams table
- Must come after SELECT

**Clause**
- Part of a SQL query
- Examples: SELECT clause, FROM clause, WHERE clause, ORDER BY clause

---

### WHERE & Filtering

**WHERE**
- Filters rows based on conditions
- Only returns rows that match your criteria
- Example: `WHERE state = 'Ohio'` — only Ohio teams
- Uses comparison operators: `=`, `!=`, `>`, `<`, `>=`, `<=`

**Condition**
- A criterion or rule for filtering
- Example: `pts >= 20` (points greater than or equal to 20)
- Can combine multiple conditions with AND/OR

**AND Operator**
- Both conditions must be true
- Example: `WHERE season = '2021-22' AND pts >= 20`
- Narrows results (more restrictive)

**OR Operator**
- At least one condition must be true
- Example: `WHERE state = 'California' OR state = 'Texas'`
- Broadens results (less restrictive)

**BETWEEN**
- Range operator for shorthand filtering
- `WHERE pts BETWEEN 15 AND 25` same as `WHERE pts >= 15 AND pts <= 25`
- Inclusive of both endpoints

---

### ORDER BY & Sorting

**ORDER BY**
- Sorts results ascending (A-Z, 0-9) or descending
- Default: ascending order
- Example: `ORDER BY pts DESC` — highest points first

**ASC (Ascending)**
- Sorts from smallest to largest or A-Z
- Default behavior (don't need to write it)
- Example: `ORDER BY year_founded` (oldest first)

**DESC (Descending)**
- Sorts from largest to smallest or Z-A
- Must explicitly write DESC
- Example: `ORDER BY pts DESC` (highest points first)

**Sort Priority**
- When sorting by multiple columns, first column is primary
- Example: `ORDER BY state, city` — sorts by state first, then city within each state

---

### LIMIT & Control

**LIMIT**
- Controls how many rows to return
- `LIMIT 10` — return first 10 rows
- Always goes at the END of query
- Useful for testing large queries

**Top N Query**
- Combines ORDER BY with LIMIT for "best" results
- Example: `ORDER BY pts DESC LIMIT 10` — top 10 scorers

---

## NBA Database Reference

### Database File
- **Location:** `nba_5seasons.db`
- **Format:** SQLite database
- **Seasons:** 2017-2022 (5 seasons of data)
- **Contains:** 30 NBA teams, 400+ players, 4,000+ games per season

### Table: `teams`

**Purpose:** Information about NBA franchises

**Key Columns:**
- `team_id` — Unique identifier for the team (numeric ID)
- `full_name` — Team's full name (e.g., "Cleveland Cavaliers")
- `abbreviation` — 3-letter code (e.g., "CLE")
- `nickname` — Team nickname (e.g., "Cavaliers")
- `city` — City where team is located
- `state` — State where team is located
- `year_founded` — Year the franchise started

**Row Count:** 30 (one per NBA team)

**Common Queries:**
```sql
-- Find teams from a state
SELECT full_name FROM teams WHERE state = 'California'

-- Find oldest teams
SELECT full_name, year_founded FROM teams ORDER BY year_founded LIMIT 5

-- Find teams founded after 1990
SELECT full_name FROM teams WHERE year_founded > 1990
```

---

### Table: `players`

**Purpose:** Lookup table for player names and IDs

**Key Columns:**
- `player_id` — Unique identifier for the player
- `full_name` — Player's full name

**Row Count:** 400+ players (across 5 seasons)

**Note:** To get player statistics, use `player_season_stats` table

---

### Table: `player_season_stats`

**Purpose:** Statistics for each player in each season

**One row per player per season** (e.g., LeBron James has 5 rows, one per season)

**Key Columns for Filtering:**
- `season` — Season (e.g., "2021-22") — always filter by this!
- `player_id` — Player ID (links to `players` table)
- `gp` — Games played (important for meaningful analysis!)

**Scoring & Shooting:**
- `pts` — Points per game (average)
- `fg_pct` — Field goal percentage (0-100)
- `fg3_pct` — 3-point percentage (0-100)
- `ft_pct` — Free throw percentage (0-100)

**Efficiency Stats:**
- `reb` — Rebounds per game (average)
- `ast` — Assists per game (average)
- `stl` — Steals per game (average)
- `blk` — Blocks per game (average)
- `tov` — Turnovers per game (average)
- `min` — Minutes per game (average)

**Common Filters:**
```sql
-- Only include players with meaningful playing time
WHERE gp >= 40

-- Elite scorers
WHERE pts >= 20 AND gp >= 40

-- Elite 3-point shooters
WHERE fg3_pct >= 40 AND gp >= 40

-- Specific season
WHERE season = '2021-22'
```

**Common Query Pattern:**
```sql
SELECT player_id, pts, reb, ast
FROM player_season_stats
WHERE season = '2021-22' AND gp >= 40
ORDER BY pts DESC
LIMIT 10
```

---

### Table: `team_game_stats`

**Purpose:** Statistics for each team in each game

**One row per team per game** (e.g., Cavaliers have ~82 rows per season)

**Key Columns for Filtering:**
- `season` — Season (e.g., "2021-22") — always filter!
- `game_id` — Unique game identifier
- `team_id` — Team ID (links to `teams` table)
- `game_date` — Date of the game
- `wl` — Win/Loss result ('W' or 'L')

**Scoring & Shooting:**
- `pts` — Points scored in the game
- `fgm` — Field goals made
- `fga` — Field goals attempted
- `fg3m` — 3-pointers made
- `fg3a` — 3-pointers attempted
- `ftm` — Free throws made
- `fta` — Free throws attempted

**Efficiency Stats:**
- `reb` — Total rebounds
- `ast` — Assists
- `stl` — Steals
- `blk` — Blocks
- `tov` — Turnovers
- `oreb` — Offensive rebounds
- `dreb` — Defensive rebounds

**Advanced:**
- `matchup` — Game description (e.g., "CLE vs. BOS")
- `plus_minus` — Point differential (+/-)

**Common Filters:**
```sql
-- Wins only
WHERE wl = 'W'

-- Losses only
WHERE wl = 'L'

-- High-scoring games
WHERE pts >= 120

-- Specific season
WHERE season = '2021-22'

-- Close games
WHERE pts BETWEEN 100 AND 110
```

**Common Query Pattern:**
```sql
SELECT game_date, pts, wl
FROM team_game_stats
WHERE season = '2021-22' AND wl = 'W'
ORDER BY pts DESC
LIMIT 20
```

---

## SQL Syntax Cheat Sheet

### Basic Query Template

```sql
SELECT   column1, column2, column3
FROM     table_name
WHERE    condition
ORDER BY column_name
LIMIT    10
```

### Comparison Operators

| Operator | Meaning | Example |
|----------|---------|----------|
| `=` | Equal | `WHERE state = 'Ohio'` |
| `!=` | Not equal | `WHERE season != '2021-22'` |
| `>` | Greater than | `WHERE pts > 20` |
| `<` | Less than | `WHERE year_founded < 1990` |
| `>=` | Greater or equal | `WHERE gp >= 40` |
| `<=` | Less or equal | `WHERE age <= 30` |

### Logical Operators

| Operator | Meaning | Example |
|----------|---------|----------|
| `AND` | Both must be true | `WHERE pts > 20 AND gp >= 40` |
| `OR` | At least one true | `WHERE state = 'CA' OR state = 'TX'` |
| `BETWEEN` | In range | `WHERE pts BETWEEN 15 AND 25` |
| `IN` | Matches list | `WHERE state IN ('CA', 'TX', 'NY')` |

### Sort Orders

```sql
ORDER BY column           -- Ascending (default)
ORDER BY column ASC       -- Ascending (explicit)
ORDER BY column DESC      -- Descending
ORDER BY col1, col2       -- Primary, then secondary
ORDER BY col1 DESC, col2  -- Primary DESC, secondary ASC
```

### Common Patterns

**Top N Query:**
```sql
SELECT * FROM table
ORDER BY column DESC
LIMIT 10
```

**Filter & Sort:**
```sql
SELECT columns
FROM table
WHERE condition
ORDER BY column
LIMIT 10
```

**Multiple Conditions:**
```sql
SELECT * FROM table
WHERE condition1 AND condition2 AND condition3
ORDER BY column
```

---

## Python + SQL Workflow

### Standard Pattern

```python
import pandas as pd
import sqlite3

# 1. Connect to database
conn = sqlite3.connect('nba_5seasons.db')

# 2. Write SQL query
query = """
SELECT full_name, pts, gp
FROM player_season_stats
WHERE season = '2021-22' AND pts >= 20 AND gp >= 40
ORDER BY pts DESC
LIMIT 10
"""

# 3. Execute query and load into pandas
df = pd.read_sql(query, conn)

# 4. Now use pandas for analysis or sklearn for ML
display(df)

# 5. Close connection when done
conn.close()
```

### Variable Naming (camelCase)

- `nbaConnection` — database connection variable
- `playerQuery` — SQL query string
- `queryResult` — result DataFrame
- `topScorersData` — specific DataFrame
- `seasonFilter` — condition string

---

## Common Mistakes & How to Fix Them

### ❌ Mistake: Forgetting quotes around text

```sql
-- WRONG
WHERE state = California
WHERE season = 2021-22

-- RIGHT
WHERE state = 'California'
WHERE season = '2021-22'
```

**Rule:** Text values need single quotes. Numbers don't.

---

### ❌ Mistake: Wrong clause order

```sql
-- WRONG
SELECT * FROM teams LIMIT 10 WHERE state = 'Texas'

-- RIGHT
SELECT * FROM teams WHERE state = 'Texas' LIMIT 10
```

**Order:** SELECT → FROM → WHERE → ORDER BY → LIMIT

---

### ❌ Mistake: Using == instead of =

```sql
-- WRONG (in SQL)
WHERE pts == 20

-- RIGHT
WHERE pts = 20
```

**Rule:** SQL uses single `=`. Double `==` is Python!

---

### ❌ Mistake: Comma after last column

```sql
-- WRONG
SELECT full_name, city, state, FROM teams

-- RIGHT
SELECT full_name, city, state FROM teams
```

**Rule:** Commas between columns, not before FROM.

---

### ❌ Mistake: Not filtering by games played

```sql
-- BAD - includes players who only played 2 games!
SELECT player_id, pts
FROM player_season_stats
WHERE pts >= 20

-- GOOD - meaningful comparison
SELECT player_id, pts, gp
FROM player_season_stats
WHERE pts >= 20 AND gp >= 40
```

**Rule:** For player stats, always check `gp >= 40` for meaningful analysis.

---

### ❌ Mistake: Forgetting to filter by season

```sql
-- BAD - mixes all 5 seasons!
SELECT player_id, pts FROM player_season_stats WHERE pts >= 20

-- GOOD
SELECT player_id, pts FROM player_season_stats
WHERE season = '2021-22' AND pts >= 20
```

**Rule:** Database has multiple seasons. Always specify which one!

---

## SQL vs. Pandas Comparison

| Operation | Pandas | SQL |
|-----------|--------|-----|
| Load data | `pd.read_csv('file.csv')` | `SELECT * FROM table` |
| Select columns | `df[['col1', 'col2']]` | `SELECT col1, col2 FROM table` |
| Filter rows | `df[df['pts'] > 100]` | `WHERE pts > 100` |
| Sort ascending | `df.sort_values('pts')` | `ORDER BY pts` |
| Sort descending | `df.sort_values('pts', ascending=False)` | `ORDER BY pts DESC` |
| First N rows | `df.head(10)` | `LIMIT 10` |
| AND condition | `df[(df['a'] > 5) & (df['b'] == 'x')]` | `WHERE a > 5 AND b = 'x'` |
| OR condition | `df[(df['a'] == 1) \| (df['b'] == 2)]` | `WHERE a = 1 OR b = 2` |

---

## Practice Examples

### Example 1: California Teams
```sql
SELECT full_name, city
FROM teams
WHERE state = 'California'
ORDER BY full_name
```

### Example 2: Top Scorers (2021-22)
```sql
SELECT player_id, pts, reb, ast, gp
FROM player_season_stats
WHERE season = '2021-22' AND pts >= 25 AND gp >= 40
ORDER BY pts DESC
LIMIT 10
```

### Example 3: High-Scoring Wins
```sql
SELECT game_date, pts, wl
FROM team_game_stats
WHERE season = '2021-22' AND pts >= 130 AND wl = 'W'
ORDER BY pts DESC
```

### Example 4: Old Teams
```sql
SELECT full_name, year_founded
FROM teams
WHERE year_founded < 1950
ORDER BY year_founded
```

### Example 5: Elite 3-Point Shooters
```sql
SELECT player_id, fg3_pct, pts, gp
FROM player_season_stats
WHERE season = '2021-22' AND fg3_pct >= 40 AND gp >= 40
ORDER BY fg3_pct DESC
```

---

## Key Concepts for Machine Learning

### Why SQL Matters for ML

1. **Memory Efficiency:** Filter data in database, load only what you need
2. **Feature Engineering:** Use GROUP BY and aggregations to create features
3. **Data Preparation:** Combine multiple tables with JOINs
4. **Scaling:** SQL scales to billion-row databases; pandas doesn't

### Feature Engineering with SQL

You can create ML features directly in SQL:

```sql
-- Feature: Scoring efficiency
SELECT team_id, (fgm * 1.0 / fga) as scoring_efficiency
FROM team_game_stats
WHERE gp >= 10

-- Feature: Turnover rate
SELECT team_id, (tov * 1.0 / pts) as turnover_rate
FROM team_game_stats

-- Grouped feature: Season average
SELECT team_id, AVG(pts) as avg_points
FROM team_game_stats
GROUP BY team_id
```

---

## Study Tips

1. **Keep SQL reference guide open** while coding
   - Even professional data scientists look up syntax
   - Bookmarks help!

2. **Test queries incrementally**
   - Get SELECT working first
   - Add WHERE conditions one at a time
   - Test LIMIT 5 before LIMIT all

3. **Read error messages carefully**
   - "Syntax error" = wrong clause order or missing comma
   - "No such column" = typo in column name
   - "Ambiguous column" = specify which table

4. **Filter by games played (gp)**
   - Essential for meaningful player statistics
   - Avoids skewed results from players with few games

5. **Filter by season**
   - Database has 5 seasons (2017-18 through 2021-22)
   - Always specify which season you want

6. **Use meaningful variable names**
   - `topScorerResults` is better than `df2`
   - `nbaConnection` is better than `conn`
   - Helps you remember what data you're working with

---

## Assessment Checklist

Before submitting work, verify:

- [ ] All SQL queries follow correct syntax (SELECT → FROM → WHERE → ORDER BY → LIMIT)
- [ ] Text values in WHERE conditions use single quotes
- [ ] Variables use camelCase naming (e.g., `queryResult`)
- [ ] Database connection is established with `sqlite3.connect()`
- [ ] Results are loaded into pandas with `pd.read_sql()`
- [ ] Code has comments explaining what each SQL clause does
- [ ] For player stats, WHERE clause includes `gp >= 40`
- [ ] For all queries, WHERE clause includes season filter
- [ ] Results are displayed and make intuitive sense

---

## Resources

**Files Provided:**
- `ai04_Walkthrough.ipynb` — Step-by-step tutorial with examples
- `ai04_Walkthrough_Solutions.ipynb` — Full solutions
- `ai04a_Task.ipynb` — Practice basic queries
- `ai04b_Task.ipynb` — Practice aggregation
- `ai04_DIYTask.ipynb` — Discover your own insights
- `SQL_Quick_Reference_ai04a.md` — Quick syntax reference

**External Resources:**
- SQLite Documentation: https://sqlite.org/docs.html
- SQL Tutorial: https://www.w3schools.com/sql/
- NBA Basketball Reference: https://www.basketball-reference.com/

---

**Version:** AI Course - ai04 SQL for Machine Learning
**Updated:** February 2026
**For:** Medina County Career Center

