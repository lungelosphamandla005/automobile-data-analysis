# Exploratory Data Analysis (EDA): Automobile Dataset

This project explores a classic automobile dataset (~205 cars) to understand how **technical specs** (engine size, horsepower, cylinders), **performance** (city/highway MPG), and **dimensions** relate to **price** and **brand/manufacturer** characteristics.

---

## 1) Goals & Key Questions
- **Data quality:** What cleaning is needed (missing values, types, duplicates)?
- **Price drivers:** How do displacement/engine size and horsepower relate to price?
- **Fuel efficiency:** Which brands are most/least efficient (city/highway MPG)?
- **Market mix:** Which manufacturers have the widest model range in this sample?
- **Body styles:** How do categories (e.g., hatchback) differ on core metrics?

---

## 2) Dataset
- File: `data/automobile.txt` (CSV-like text used in many EDA tutorials)
- Rows: ~205; Columns: ~24 (make, body-style, engine-type, cylinders, engine-size, horsepower, peak-rpm, mpg, price, etc.)
- Quirks: Missing values encoded as `"?"`; some numeric fields stored as text.

---

## 3) Methods (Notebook Workflow)
- **Load & Inspect:** preview, schema, descriptive stats.
- **Cleaning:**
  - Drop low-value fields: `normalized-losses`, `symboling`.
  - Convert `"?"` → `NaN` and drop rows with missing **critical numeric** fields (e.g., bore, stroke, horsepower, peak-rpm, price).
  - Standardize dtypes: coerce numerics; cast selected columns to `int64` where appropriate.
  - De-duplicate rows (sanity check).
- **Feature handling:**
  - Build convenience subsets (e.g., hatchbacks).
  - Compute combined efficiency: `avg_mpg = (city-mpg + highway-mpg)/2`.
- **Analysis & Visualization (matplotlib):**
  - Bar charts: **Top-5 most expensive vs least expensive** (price).
  - Grouped bars: **City vs Highway MPG** for selected models and by **manufacturer**.
  - Counts by make: which brands have the **most models**.
  - Scatterplots: Price vs **City/Highway/Avg MPG**.

---

## 4) Main Findings (at a glance)
- **Luxury/performance trade-off:** Top-priced brands (e.g., Mercedes-Benz, BMW, Porsche) show **low MPG** (city ≈ 14–17; highway ≈ 16–25). Budget models (e.g., Subaru, Chevrolet, Mazda, Toyota, Mitsubishi) show **high MPG** (city ≈ 31–47; highway ≈ 36–53).
- **Engine size & efficiency:** Larger engines correlate with **higher prices** and **lower MPG**.
- **Most models in sample:** **Toyota (~32)** leads model count, indicating broad coverage in this dataset.
- **Category snapshot:** ~63 **hatchbacks** identified; useful for focused comparisons.

> Interpretation: Price tends to cluster with displacement/brand positioning; efficiency separates economy vs luxury segments.

---

