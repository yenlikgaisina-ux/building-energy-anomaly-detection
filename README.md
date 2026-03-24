# Building Energy Anomaly Detection

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python&logoColor=white) ![Status](https://img.shields.io/badge/Status-Complete-brightgreen) ![Data](https://img.shields.io/badge/Data-UK%20EPC%20Open%20Data-orange) ![License](https://img.shields.io/badge/License-MIT-lightgrey)

> **Detecting anomalously energy-inefficient homes across England & Wales to support government retrofit investment decisions.**

---

## Business Question

> *Which residential buildings in England and Wales are anomalously energy-inefficient, and how can local authorities and retrofit programmes prioritise them for intervention?*

The UK government has committed to improving the energy efficiency of homes to meet net-zero targets. With millions of EPC (Energy Performance Certificate) records publicly available, this project applies anomaly detection techniques to identify buildings that fall outside expected efficiency patterns — flagging them as priority candidates for retrofit investment.

---

## Dataset

| Property | Detail |
|----------|--------|
| **Source** | [UK Government EPC Open Data](https://epc.opendatacommunities.org/) — MHCLG |
| **Coverage** | England and Wales, domestic properties |
| **Format** | CSV, publicly available, open licence |

**Features used:** `current_energy_efficiency`, `energy_consumption_current` (kWh/m²/yr), `co2_emissions_current` (t CO2/yr), `total_floor_area` (m²), `heating_cost_current`, `hot_water_cost_current`, `lighting_cost_current`

---

## Methodology

Two complementary anomaly detection approaches are applied so results can be cross-validated without labelled ground truth.

| Method | Type | How it works |
|--------|------|-------------|
| **IQR (Interquartile Range)** | Statistical | Flags properties where multiple features simultaneously exceed IQR bounds — calibrated to capture the top 1–5% of outliers per feature |
| **Isolation Forest** | Machine learning | Unsupervised ensemble that isolates anomalies by random feature partitioning; buildings requiring fewer splits to isolate are scored as more anomalous |
| **PCA** | Dimensionality reduction | Reduces 7 features to 2 principal components for visual separation of anomalous vs normal records |

---

## Key Results

| Metric | Value |
|--------|-------|
| Properties flagged as anomalous | ~2.3% of total dataset |
| Energy consumption vs median | 3–5x higher in anomalous buildings |
| CO2 emissions: flagged vs normal | 4.1 t/yr vs 1.8 t/yr |
| Highest anomaly concentration | Pre-1930, solid wall, no insulation |
| Method agreement (IQR & Isolation Forest) | ~78% of flagged cases |

### PCA Separation: Normal vs Anomalous Buildings

The PCA projection below shows clear separation between flagged and unflagged properties along PC1, which loads most strongly on energy consumption and CO2 emissions.

![PCA separation chart](docs/pca_separation.png)

### Anomaly Score Distribution

Buildings in the top-right cluster combine high energy consumption with high CO2 emissions relative to floor area — the profile most consistent with pre-1930 solid-wall construction without insulation.

![Anomaly distribution chart](docs/anomaly_distribution.png)

### Retrofit Prioritisation Output

The chart below shows the concentration of flagged properties by construction era and wall type — the two variables with strongest association with anomalous EPC scores.

![Retrofit prioritisation chart](docs/retrofit_priority.png)

---

## What Local Authorities Should Do With This Output

| Step | Action |
|------|--------|
| 1 | Cross-reference flagged properties against tenure data to identify households eligible for **ECO4** or the **Great British Insulation Scheme** |
| 2 | Prioritise outreach and surveying to the top anomaly confidence tier (IQR + Isolation Forest agreement) |
| 3 | Estimate potential CO2 reduction per intervention using the predicted efficiency gap |
| 4 | Report impact metrics to central government funding bodies |

---

## Repository Structure

```
building-energy-anomaly-detection/
|-- notebook/
|   +-- building_energy_anomaly_detection.ipynb
|-- docs/
|   +-- pca_separation.png
|   +-- anomaly_distribution.png
|   +-- retrofit_priority.png
+-- README.md
```

---

## Skills Demonstrated

`Python` `Pandas` `NumPy` `Scikit-learn` `IQR` `Isolation Forest` `PCA` `Matplotlib` `Seaborn` `EPC Open Data` `Anomaly Detection` `Sustainability Analytics`

---

## Author

**Yenlik Gaisina** | Data & Analytics Consultant
[LinkedIn](https://www.linkedin.com/in/yenlik-gaisina/) | Cambridge Data Science with ML & AI Programme
