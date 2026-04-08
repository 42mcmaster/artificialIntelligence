# Dataset Guide — Linear Regression Assignment

Pick one of these four datasets for your assignment. Each one comes from the UCI Machine Learning Repository and can be loaded with a single line of Python. They range from easy to hard depending on how much cleaning is needed and how well linear regression fits the data.

Read through the descriptions below and pick the one that sounds most interesting to you. There's no wrong choice — but if you want a smoother experience, start with Real Estate or Wine Quality.

---

## Real Estate Valuation (UCI id=477) — Easy

**What you're predicting:** House price per unit area (in Taiwanese dollars per ping)

**What's in the data:** 414 houses from New Taipei City, Taiwan with 6 features — house age, distance to the nearest MRT (subway) station, number of nearby convenience stores, transaction date, and geographic coordinates (latitude/longitude).

**Why pick this one:** It's small, fully numeric, has no missing values, and the relationships are intuitive. Distance to public transit is the strongest predictor — closer to an MRT station means higher prices, which makes immediate real-world sense. The small number of features means your heatmap is easy to read and the multicollinearity decisions are straightforward. If you want to focus on learning the process without fighting the data, this is your best bet.

**What to watch for:** Latitude and longitude both correlate with distance to MRT (they're all measuring location), so there's some mild multicollinearity. You'll need to decide whether that's enough to warrant dropping anything from an already small feature set. Expected R² is around 0.55–0.70.

---

## Wine Quality (UCI id=186) — Medium

**What you're predicting:** Wine quality score (rated 1–10 by human tasters)

**What's in the data:** 4,898 white wines from northern Portugal with 11 chemical measurements — acidity levels, sugar content, sulfur dioxide, density, pH, alcohol content, and more.

**Why pick this one:** The features are all numeric, there are no missing values, and the dataset is large enough that you won't worry about running out of data. The chemistry angle is interesting — you get to find out which chemical properties actually make wine taste better (spoiler: alcohol content matters a lot). It's also a good lesson in humility, because the R² will be low (around 0.25–0.30). Wine quality is subjective and driven by factors that chemistry alone can't capture.

**What to watch for:** Density is a trap — it's essentially a mathematical combination of residual sugar and alcohol (basic chemistry), so it's redundant. Free sulfur dioxide overlaps with total sulfur dioxide. If you include everything, the multicollinearity won't be catastrophic, but you'll see some coefficient instability. The low R² isn't a failure on your part — it just means this problem is genuinely hard for linear regression.

---

## Abalone (UCI id=1) — Medium

**What you're predicting:** Age of an abalone (a type of sea snail), measured by counting rings in the shell — similar to counting tree rings.

**What's in the data:** 4,177 abalones with 8 features — sex (male/female/infant), length, diameter, height, and four weight measurements (whole weight, shucked weight, viscera weight, shell weight).

**Why pick this one:** If biology or marine science interests you, this is a cool dataset. The whole reason it exists is that counting rings under a microscope is tedious and expensive, so researchers wanted to know if simple physical measurements could predict age instead. You also get to deal with the most extreme multicollinearity of any of these datasets — all the size and weight measurements are correlated with each other at r = 0.80 to 0.97, which gives you a very clear multicollinearity decision to make.

**What to watch for:** The `Sex` column is categorical (M, F, or I for infant), so you'll need to drop it since we haven't covered encoding categorical variables yet. The multicollinearity is severe — all the numeric features are essentially measuring "how big is this abalone?" Shell weight has the strongest individual correlation with rings, so you might end up doing simple regression with just that one feature (similar to what we did with weight in the class example). Expected R² is around 0.35–0.40, which again reflects the difficulty of the problem, not a failure of your model.

---

## Automobile (UCI id=10) — Hard

**What you're predicting:** Car price

**What's in the data:** 205 cars from the 1985 Ward's Automotive Yearbook with 25 features covering everything from engine specs to body style to fuel system.

**Why pick this one:** If you want a challenge and want to practice data cleaning, this is the one. It's the messiest dataset of the four — multiple columns have missing values, and 10 of the 25 features are categorical (text like "sedan", "diesel", "honda") that you'll need to drop. After cleaning, you'll be working with roughly 160 rows and about 15 numeric features, many of which are heavily intercorrelated. But the payoff is decent — engine size and curb weight are strong predictors of price, and you can get R² around 0.75–0.85.

**What to watch for:** You'll lose about 40 rows just from dropping missing values, which is significant when you only started with 205. `city-mpg` and `highway-mpg` are nearly identical (r ≈ 0.97) — definitely drop one. Engine size, curb weight, horsepower, width, and length all form a big multicollinearity cluster. You'll need to be aggressive about feature selection. The small dataset also means your test set will only have about 30–35 cars, so your R² might bounce around depending on the random split.

---

## Quick Comparison

| | Real Estate | Wine Quality | Abalone | Automobile |
|---|---|---|---|---|
| **Rows** | 414 | 4,898 | 4,177 | 205 |
| **Features** | 6 | 11 | 8 | 25 |
| **Missing values** | None | None | None | Several columns |
| **Non-numeric columns** | None | None | 1 (Sex) | 10 |
| **Cleaning needed** | Minimal | Minimal | Drop Sex column | Heavy |
| **Multicollinearity** | Mild | Moderate | Severe | Severe |
| **Expected R²** | 0.55–0.70 | 0.25–0.30 | 0.35–0.40 | 0.75–0.85 |
| **Best for** | Learning the process | Large dataset, low R² lesson | Biology interest, clear multicollinearity | Data cleaning practice |
