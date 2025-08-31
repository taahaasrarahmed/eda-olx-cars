# 🚗 OLX Cars EDA (Pakistan)

Exploratory data analysis of used-car listings from OLX Pakistan.  
We study how **price** varies with **mileage, model year, brand, transmission, and location**, and fit a simple baseline model.

---

## 🔎 Highlights (your results)

- **Price spread:** wide; mean pulled up by high-end tail (see boxplot & brand means).
- **Mileage effect:** clear negative trend; stronger in Honda/Toyota than Suzuki/Hyundai/Mitsubishi.
- **Year (age):** strongest driver; newer models command a steep premium.
- **City gap:** Lahore prices generally above Karachi across mileage bins; gap narrows at very high mileage.
- **Break-even mileage (piecewise slope change):** **≈ 17,161 km**.
- **Baseline model (Random Forest):** **R² = 0.951**, **MAPE = 9.64%** ✅ (<10%).

---

## 📊 Key Questions & Figures

### 1) What does the overall price distribution look like?
- Boxplot shows median around ~1.8M PKR with long right tail.
- Top-10 makes by mean price confirm brand mix (Mercedes/Toyota/Honda higher tier).
  
![Boxplot of prices](reports/01/boxplot_prices.png)
![Top makes by average price](01/figures/price_brands.png)

---

### 2) How does mileage impact price?
- Brand-wise scatter makes the downward slope visible; strongest for Honda/Toyota.
- Transmission split: automatics list higher on average; both show price drop with mileage.
  
![Mileage vs price by brand](reports/02/mileage_price.png)
![Mileage vs price by transmission](reports/02/mileage_price_transmission.png)

**Break-even mileage:** using piecewise linear regression, the slope steepens after **≈ 17,161 km**, i.e., price declines faster beyond this point.  
(Notebook: `notebooks/break_even_mileage.ipynb`)

---

### 3) How does model year affect price?
- Newer model years command much higher prices; year is the strongest single driver.
- Brand-wise panels show similar shape with different levels.
  
![Price vs model year (overall)](reports/03/year_price.png)
![Price vs model year by brand](reports/03/year_price_model.png)

---

### 4) Is there a city effect (Karachi vs Lahore) across mileage?
- Lahore > Karachi across most mileage bins; the gap diminishes at very high mileage.
  
![City comparison over mileage bins](reports/04/mileage_price_location.png)

---

### 5) Which features matter most?
- Correlations: **Year (+)** strongest; **Mileage (−)** moderate; **Transmission (−)** shows price tiering effects.
- Brand-wise correlations echo the pattern (Honda/Toyota show stronger |corr| with year/mileage).
  
![Correlation with price (overall)](reports/05/feature_selection.png)
![Correlation with price by brand](reports/05/feature_selection_model.png)

---

### 6) Can we predict price reasonably well?
- **Random Forest** baseline on held-out data:  
  - **R²:** `0.9506742203449255`  
  - **MAPE:** `0.09638845487934829` (**9.64%**) ✅

(Notebook: `notebooks/price_pred_randFor.ipynb`)

---

## 🗂️ Project Structure

