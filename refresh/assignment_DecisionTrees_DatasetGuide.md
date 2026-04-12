# Dataset Guide — Decision Trees Classification Assignment

Pick one of these three datasets for your assignment. Each one is a classification problem — you're predicting a **category**, not a number. They range from easy to hard depending on how many classes there are, how much cleaning is needed, and how well the tree can separate things.

Read through the descriptions below and pick the one that sounds most interesting to you. There's no wrong choice — but if you want a smoother experience, start with Palmer Penguins.

---

## Palmer Penguins (seaborn built-in) — Easy

**What you're predicting:** Penguin species (Adelie, Chinstrap, or Gentoo)

**What's in the data:** 344 penguins measured at Palmer Station in Antarctica with 4 numeric features — bill length (mm), bill depth (mm), flipper length (mm), and body mass (g). There are also two non-numeric columns (island and sex) that you'll need to drop since we haven't covered encoding.

**How to load:**
```python
import seaborn as sns
df = sns.load_dataset('penguins')
```

**Why pick this one:** It's small, mostly numeric, and the three species separate cleanly — similar to how Iris worked in the class walkthrough. The decision tree should get 95%+ accuracy without much effort. The scatter plots look great (bill length vs flipper length gives you really obvious clusters). If you want to focus on learning the classification process without fighting the data, this is your best bet.

**What to watch for:** There are about 10 rows with missing values — you'll need to `dropna()` before doing anything. You also need to drop the `island` and `sex` columns since they're text, not numbers. After that, it's smooth sailing. The tree visualization will be easy to read with just 3 classes and 4 features.

---

## Breast Cancer Wisconsin Diagnostic (sklearn built-in) — Medium

**What you're predicting:** Whether a tumor is Malignant or Benign (binary — 2 classes)

**What's in the data:** 569 tumor samples with 30 numeric features computed from cell nucleus images — things like radius, texture, perimeter, area, smoothness, compactness, and symmetry. Each measurement has a mean, standard error, and worst-case value, giving you 10 base measurements × 3 = 30 features.

**How to load:**
```python
from sklearn.datasets import load_breast_cancer
cancer = load_breast_cancer(as_frame=True)
X = cancer.data
y = cancer.target
df = X.copy()
df['diagnosis'] = y
```

**Why pick this one:** The data is completely clean (no missing values, all numeric), so you can focus on the modeling. The real challenge is that 30 features is a LOT. Your feature importance chart will be interesting — you'll see that the tree only actually uses a handful of those 30 features to make decisions. The medical context makes it feel meaningful — you're building something that could help detect cancer. Accuracy should land around 93–97%.

**What to watch for:** Many of the 30 features are highly correlated with each other (radius, perimeter, and area are all measuring "how big is the cell," just in different ways). The tree handles this fine on its own (it just picks the best one), but it's worth noticing in your exploration. With only 2 classes, the confusion matrix is a simple 2×2 grid, which makes it easy to see exactly how many false positives and false negatives you get.

---

## Wine Recognition (sklearn built-in) — Easy-Medium

**What you're predicting:** Which cultivar (vineyard/grape grower) produced the wine — 3 classes (labeled 0, 1, 2 in sklearn)

**What's in the data:** 178 Italian wines from 3 different cultivars in the same region of Italy, with 13 chemical measurements — alcohol, malic acid, ash, alcalinity of ash, magnesium, total phenols, flavanoids, nonflavanoid phenols, proanthocyanins, color intensity, hue, OD280/OD315 of diluted wines, and proline.

**How to load:**
```python
from sklearn.datasets import load_wine
wine = load_wine(as_frame=True)
X = wine.data
y = wine.target
df = X.copy()
df['cultivar'] = y
```

**Why pick this one:** It's clean (all numeric, no missing values), the 3 classes are roughly balanced, and the tree should get 90%+ accuracy. With 13 features your feature importance chart tells an interesting story — some chemicals matter a lot for telling the cultivars apart and others barely register. The idea that a wine's chemical "fingerprint" reveals where it was grown is a cool real-world application.

**What to watch for:** This is a DIFFERENT dataset than the Wine Quality one you may have used for the linear regression assignment. Wine Quality predicts a quality *score* — a number from 1 to 10 (regression). Wine Recognition (this one) predicts which *cultivar* grew the grapes — a category (classification). Don't mix them up! The sklearn labels are generic (`class_0`, `class_1`, `class_2`) — these just mean Cultivar 1, 2, and 3 from the original Italian wine study. With only 178 samples the dataset is small, so your test set will be about 36 wines. Accuracy can shift a few points depending on the random split, but it should stay above 85%.

---

## Quick Comparison

| | Palmer Penguins | Wine Recognition | Breast Cancer |
|---|---|---|---|
| **Source** | seaborn (built-in) | sklearn (built-in) | sklearn (built-in) |
| **Rows** | 344 | 178 | 569 |
| **Features** | 4 numeric + 2 to drop | 13 numeric | 30 numeric |
| **Classes** | 3 (species) | 3 (cultivars) | 2 (M vs B) |
| **Missing values** | ~10 rows | None | None |
| **Non-numeric columns** | 2 (island, sex) | None | None |
| **Class balance** | Balanced | Balanced | Slightly imbalanced |
| **Expected accuracy** | 95%+ | 90–95% | 93–97% |
| **Best for** | Learning the process | Chemistry angle, clean data | Lots of features, medical context |
