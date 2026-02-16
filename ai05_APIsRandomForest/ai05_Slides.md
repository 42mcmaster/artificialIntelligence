---
marp: true
theme: default
paginate: true
---

# Lesson ai05: APIs & Random Forest
## How to Fetch Data + Build Better Models

**Medina County Career Center**
AI/ML Course — Unit 2 Final Lesson

---

# Part 1: APIs — Getting Live Data

## What is an API?

**API = Application Programming Interface**

Think of it like ordering at a restaurant:

| Restaurant | API |
|-----------|-----|
| Menu | API docs |
| Your order | HTTP request |
| Waiter | API endpoint |
| Kitchen | Server/database |
| Your food | JSON response |

**You don't go into the kitchen yourself — the waiter handles it.**

---

# Why APIs Matter

**Without APIs:** Download files manually, hope they're current, copy/paste into Python.

**With APIs:** Get live data programmatically — weather, earthquakes, sports, crypto, any public data.

**Real use:** ML models need fresh data. APIs deliver it automatically.

---

# URL Structure

```
https://api.example.com/v1/data?key=value&limit=10
└─────┬──────┘ └────┬────┘  └──┬──┘ └──────┬──────┘
 Protocol      Host         Path   Parameters
```

**Parameters filter data:**
- `?` starts parameters
- `key=value` format
- `&` separates multiple parameters

**Test URLs in your browser!**

---

# Example: USGS Earthquakes API

```
https://earthquake.usgs.gov/fdsnws/event/1/query?
  format=geojson&
  minmagnitude=6.0&
  limit=5
```

This fetches: earthquakes with magnitude 6.0+, max 5 results, as GeoJSON.

---

# What is JSON?

**JSON = JavaScript Object Notation** — how APIs send data back.

```json
{
  "earthquakes": [
    {
      "magnitude": 7.2,
      "location": "Japan",
      "depth_km": 25
    }
  ]
}
```

Python reads JSON instantly with `.json()`

---

# Fetching Data with Python

```python
import requests                    # Fetch data from internet

baseUrl = "https://api.example.com/data"
params = {
    "latitude": 41.14,             # Medina, OH
    "longitude": -81.86,
    "days": 7
}

response = requests.get(baseUrl, params=params)
data = response.json()             # JSON → Python dict
```

That's it! Now `data` contains the API response as a dictionary.

---

# From JSON to DataFrames

```python
import pandas as pd

# Flatten nested JSON into a DataFrame
df = pd.DataFrame(data['records'])

print(df.shape)       # See dimensions
print(df.columns)     # See column names
print(df.head())      # Preview data
```

Now you have structured data ready for ML!

---

# Part 2: Random Forest — Ensemble Learning

## One Tree vs. Many Trees

**Single Decision Tree:** One expert makes the decision.
- Fast, simple
- Can overfit (memorize noise)
- May miss patterns

**Random Forest:** 100 experts vote.
- More accurate
- Harder to overfit
- Shows which features matter most

---

# How Random Forest Works

### Two Layers of Randomness:

1. **Random Samples:** Each tree trains on ~500-game bootstrap sample (random subset WITH replacement)

2. **Random Features:** At each split, tree considers only random 3 of 7 features

### Result:
- 100 diverse trees trained on different data + different features
- Trees vote: majority wins
- Predictions are more robust

---

# Real Example: Predicting NBA Wins

**Question:** Can we predict if the home team wins using game statistics?

**Features (differentials):**
- Points differential (PTS_diff)
- Rebounds differential (REB_diff)
- Assists differential (AST_diff)
- Field goal % differential (FG%_diff)
- Turnovers differential (TOV_diff)
- Steals differential (STL_diff)

**Baseline:** Always predict "home wins" = 54% accuracy
**Random Forest:** 62-66% accuracy ✓

---

# Feature Importance

```python
forestModel.feature_importances_
```

Shows which stats matter most for winning:

```
AST_diff:    0.28  ← Most important!
FG%_diff:    0.25
PTS_diff:    0.22
REB_diff:    0.15
TOV_diff:    0.08
STL_diff:    0.02  ← Least important
```

**Insight:** Assists and field goal % predict wins better than steals.

---

# Building a Random Forest

```python
from sklearn.ensemble import RandomForestClassifier

# Create the forest (100 trees by default)
forestModel = RandomForestClassifier(n_estimators=100, random_state=42)

# Train on NBA data
forestModel.fit(xTrain, yTrain)

# Get predictions
predictions = forestModel.predict(xTest)

# Check accuracy
from sklearn.metrics import accuracy_score
acc = accuracy_score(yTest, predictions)
print(f"Accuracy: {acc:.2%}")
```

**That's the complete workflow!**

---

# Key Takeaways

## APIs:
✓ Automate data collection
✓ Get live, current data
✓ Build reproducible pipelines

## Random Forest:
✓ Ensemble = many weak learners → strong model
✓ Randomness prevents overfitting
✓ Feature importance reveals insights
✓ Simple to use, hard to break

**Next:** Build your own API queries and train forests on real data!
