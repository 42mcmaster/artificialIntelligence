# ai05 Study Guide: APIs & Random Forest

## Vocabulary (15 key terms)

1. **API** — Application Programming Interface; a contract between a client and server for requesting data
2. **Endpoint** — The specific path on an API server (e.g., `/weather`, `/earthquakes`)
3. **HTTP Request** — A message sent to a server asking for data (GET, POST, PUT, DELETE)
4. **JSON** — JavaScript Object Notation; a text format for sending structured data (key-value pairs)
5. **Key-Value Pair** — `"name": "Alice"` — connects a label to a value
6. **Parameter** — A query variable that filters API results (e.g., `?limit=10&sort=date`)
7. **Response** — The data sent back by an API after a successful request
8. **Status Code** — Tells you if the request succeeded (200 = success, 404 = not found, 500 = server error)
9. **Ensemble Learning** — Combining multiple weak models into one strong model
10. **Bagging** — Bootstrap Aggregating; training models on random subsets of data with replacement
11. **Bootstrap Sample** — A random sample of data taken WITH replacement (same data can appear twice)
12. **Feature Importance** — A ranking showing which input features matter most for predictions
13. **Random Forest** — An ensemble of decision trees, each trained on random data + random features
14. **Majority Voting** — In a forest, the most common prediction from trees becomes the final prediction
15. **Overfitting** — When a model memorizes training data instead of learning general patterns

---

## Quick Reference: Using `requests` Library

### Basic API Call Pattern

```python
import requests                              # Import requests to fetch data
import pandas as pd                          # Import pandas to work with DataFrames

# Step 1: Define the base URL and parameters
baseUrl = "https://api.example.com/data"
params = {
    "latitude": 41.14,                       # Medina, OH
    "longitude": -81.86,
    "days": 7
}

# Step 2: Send the GET request
response = requests.get(baseUrl, params=params)

# Step 3: Check if request succeeded
if response.status_code == 200:
    data = response.json()                   # Convert JSON to Python dict
    print("Success! Got data.")
else:
    print(f"Error {response.status_code}")

# Step 4: Convert to DataFrame
df = pd.DataFrame(data['records'])
print(df.head())
```

### HTTP Status Codes

| Code | Meaning | Action |
|------|---------|--------|
| 200 | OK — success | Use the data |
| 400 | Bad Request — wrong parameters | Fix your params |
| 404 | Not Found — endpoint doesn't exist | Check the API docs |
| 500 | Server Error — not your fault | Try again later |

---

## Quick Reference: Random Forest Classifier

### Training a Model

```python
from sklearn.ensemble import RandomForestClassifier  # The forest algorithm
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, classification_report

# Step 1: Load data and split into features (X) and target (y)
nbaData = pd.read_csv('nba_win_prediction.csv')
X = nbaData[['pts_diff', 'reb_diff', 'ast_diff', 'fg_pct_diff', 'tov_diff', 'stl_diff']]
y = nbaData['home_win']                      # 1 = home team won, 0 = home team lost

# Step 2: Train-test split (80% train, 20% test)
xTrain, xTest, yTrain, yTest = train_test_split(X, y, test_size=0.2, random_state=42)

# Step 3: Create and train the forest
forestModel = RandomForestClassifier(
    n_estimators=100,                        # Number of trees (more = better, slower)
    random_state=42                          # For reproducible results
)
forestModel.fit(xTrain, yTrain)              # Train all 100 trees

# Step 4: Make predictions
predictions = forestModel.predict(xTest)     # Get predictions on test data

# Step 5: Evaluate performance
accuracy = accuracy_score(yTest, predictions)
print(f"Accuracy: {accuracy:.2%}")

# Step 6: Get feature importance
featureImportance = pd.DataFrame({
    'Feature': X.columns,
    'Importance': forestModel.feature_importances_
}).sort_values('Importance', ascending=False)

print(featureImportance)
```

### Key Parameters

| Parameter | Default | Meaning |
|-----------|---------|---------|
| `n_estimators` | 100 | Number of trees in the forest |
| `max_depth` | None | Maximum depth of each tree (None = unlimited) |
| `random_state` | None | Seed for reproducibility |
| `test_size` | 0.2 | Fraction of data to use for testing (20%) |

---

## Common Mistakes & Fixes

### APIs

**Mistake:** Forgetting to convert JSON to DataFrame
```python
# ❌ Wrong
data = response.json()
print(data[0])  # Won't work if data is a dict

# ✓ Correct
data = response.json()
df = pd.DataFrame(data['records'])
print(df.head())
```

**Mistake:** Wrong parameter format
```python
# ❌ Wrong
params = "latitude=41.14&longitude=-81.86"  # String, not dict!

# ✓ Correct
params = {
    "latitude": 41.14,
    "longitude": -81.86
}
```

### Random Forest

**Mistake:** Forgetting to split into X and y
```python
# ❌ Wrong
forestModel.fit(nbaData, 'home_win')  # Target shouldn't be a string!

# ✓ Correct
X = nbaData.drop('home_win', axis=1)
y = nbaData['home_win']
forestModel.fit(X, y)
```

**Mistake:** Using train data to evaluate
```python
# ❌ Wrong — evaluates on training data (misleading!)
predictions = forestModel.predict(xTrain)
accuracy = accuracy_score(yTrain, predictions)

# ✓ Correct — evaluates on test data (realistic!)
predictions = forestModel.predict(xTest)
accuracy = accuracy_score(yTest, predictions)
```

---

## Comparison: Single Tree vs. Random Forest

| Aspect | Single Tree | Random Forest |
|--------|------------|---------------|
| **Training Speed** | Fast | Slower |
| **Accuracy** | ~60% | ~65% |
| **Overfitting Risk** | High | Low |
| **Interpretability** | Easy (one path) | Hard (100 paths) |
| **Feature Importance** | Simple | More reliable |
| **Real-world use** | Rare | Common |

---

## API Practice: Free Public APIs

### Open-Meteo Weather API (no key required!)
```
https://api.open-meteo.com/v1/forecast?latitude=41.14&longitude=-81.86&hourly=temperature_2m
```

### USGS Earthquake API (no key required!)
```
https://earthquake.usgs.gov/fdsnws/event/1/query?format=geojson&minmagnitude=5.0&limit=10
```

### Open Library API (no key required!)
```
https://openlibrary.org/search.json?title=python&limit=5
```

Test these URLs directly in your browser first!

---

## ODE Competencies Covered

- **2.14.1** — Apply machine learning concepts to solve real-world problems
- **2.14.5** — Use APIs to retrieve and process structured data
- **5.1.2** — Write clean, well-commented code for team collaboration

---

## Quick Checklist Before Submission

### API Tasks
- [ ] Built correct URL with parameters
- [ ] Tested URL in browser first
- [ ] Handled JSON response correctly
- [ ] Parsed into DataFrame
- [ ] Code is heavily commented

### Random Forest Tasks
- [ ] Split data into train/test
- [ ] Trained forest with n_estimators=100
- [ ] Made predictions on test data (NOT train!)
- [ ] Calculated and reported accuracy
- [ ] Extracted and interpreted feature importance
- [ ] Compared to single tree baseline

---

## Resources

**For Help with APIs:**
- Open-Meteo docs: https://open-meteo.com/en/docs
- USGS Earthquake docs: https://earthquake.usgs.gov/fdsnws/event/1/
- `requests` library docs: https://requests.readthedocs.io/

**For Help with Random Forest:**
- sklearn docs: https://scikit-learn.org/stable/modules/ensemble.html#random-forests
- Feature importance: https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html#sklearn.ensemble.RandomForestClassifier.feature_importances_
