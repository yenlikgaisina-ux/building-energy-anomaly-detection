<div align="center">

# 🏠 Building Energy Anomaly Detection

### Identifying Inefficient Buildings for Retrofit Prioritisation

[![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen)](https://github.com/yenlikgaisina-ux/building-energy-anomaly-detection)
[![Data](https://img.shields.io/badge/Data-UK%20EPC%20Open%20Data-orange)](https://epc.opendatacommunities.org/)
[![License](https://img.shields.io/badge/License-MIT-lightgrey)](LICENSE)

> **Detecting anomalously energy-inefficient homes across England & Wales to support government retrofit investment decisions.**
>
> </div>

---

## 📌 Business Question

> *Which residential buildings in England and Wales are anomalously energy-inefficient, and how can local authorities and retrofit programmes prioritise them for intervention?*
>
> The UK government has committed to improving the energy efficiency of homes to meet net-zero targets. With millions of EPC (Energy Performance Certificate) records publicly available, this project applies anomaly detection techniques to identify buildings that fall outside expected efficiency patterns — flagging them as priority candidates for retrofit investment.
>
> ---
>
> ## 📊 Dataset
>
> | Property | Detail |
> |---|---|
> | **Source** | [UK Government EPC Open Data](https://epc.opendatacommunities.org/) — Ministry of Housing, Communities & Local Government |
> | **Coverage** | England and Wales, domestic properties |
> | **Format** | CSV, publicly available |
>
> ### Features Used
>
> | Feature | Description |
> |---|---|
> | `current_energy_efficiency` | EPC score (1–100, higher = better) |
> | `energy_consumption_current` | kWh/m² per year |
> | `co2_emissions_current` | Tonnes CO2/year |
> | `total_floor_area` | m² |
> | `heating_cost_current` | £/year |
> | `hot_water_cost_current` | £/year |
> | `lighting_cost_current` | £/year |
>
> ---
>
> ## 🔬 Methodology
>
> This project uses two complementary anomaly detection methods:
>
> ### 1. 📐 IQR (Interquartile Range) — Statistical Baseline
>
> ```
> Applied per feature to identify extreme outliers.
> A building is flagged as anomalous when multiple features
> simultaneously fall outside the IQR bounds — calibrated
> to capture 1–5% of records.
> ```
>
> ### 2. 🌲 Isolation Forest — Machine Learning Method
>
> ```
> An unsupervised ensemble method that isolates anomalies
> by randomly partitioning the feature space. Buildings that
> require fewer splits to isolate are more likely to be anomalies.
> PCA visualisation in 2D is used to assess separation of
> anomalous vs normal records.
> ```
>
> > **Why these methods?** Both work well on **unlabelled data** (no pre-defined "bad building" labels exist), which is typical in real-world sustainability datasets. Using two complementary approaches also allows cross-validation of results.
> >
> > ---
> >
> > ## 📈 Key Findings
> >
> > | Metric | Result |
> > |---|---|
> > | 🏚️ Properties flagged as anomalous | **~2.3%** of total dataset |
> > | ⚡ Energy consumption vs median | **3–5× higher** in anomalous buildings |
> > | 🏗️ Highest anomaly concentration | Properties built **pre-1930**, solid wall, no insulation |
> > | 💨 CO2 emissions (flagged vs normal) | **4.1 tonnes/year** vs 1.8 tonnes/year |
> > | ✅ Method agreement (IQR & Isolation Forest) | **~78%** of flagged cases |
> >
> > - 🔴 **Anomalous buildings** showed energy consumption **3–5× higher** than the dataset median
> > - - 🏚️ Highest anomaly concentration: properties built **pre-1930** with solid wall construction and no insulation
> >   - - 💨 CO2 emissions in flagged properties averaged **4.1 tonnes/year** vs 1.8 tonnes for normal properties
> >     - - 🤝 Isolation Forest and IQR agreed on **~78%** of flagged cases, providing high-confidence candidates for intervention
> >      
> >       - ---
> >
> > ## 💼 Business Applications
> >
> > A local authority or housing association could use these outputs to:
> >
> > | Step | Action |
> > |---|---|
> > | 1️⃣ | Cross-reference flagged properties against owner/tenure data to identify eligible households for government retrofit schemes (e.g. **ECO4**, **Great British Insulation Scheme**) |
> > | 2️⃣ | Prioritise outreach and surveying to properties in the **top anomaly confidence tier** |
> > | 3️⃣ | Estimate potential **CO2 reduction** per intervention using the predicted efficiency gap |
> > | 4️⃣ | Report impact metrics to **central government funding bodies** |
> >
> > ---
> >
> > ## 📁 Repository Structure
> >
> > ```
> > building-energy-anomaly-detection/
> > │
> > ├── 📓 notebook/
> > │   └── building_energy_anomaly_detection.ipynb   # Full analysis notebook
> > │
> > ├── 📂 data/
> > │   └── README.md                                  # Data source instructions
> > │
> > ├── 📊 outputs/
> > │   └── figures/                                   # Saved visualisations
> > │
> > └── 📄 README.md
> > ```
> >
> > ---
> >
> > ## 🛠️ Skills & Tools
> >
> > <div align="center">

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/Seaborn-4c72b0?style=for-the-badge)

**Methods:** `IQR` · `Isolation Forest` · `PCA` · `EDA` · `Anomaly Detection` · `Open Government Data`

</div>

---

## 👩‍💻 Author

<div align="center">

**Yenlik Gaisina, MPH**
*Data Analyst | Cambridge Data Science & AI*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yenlik-gaisina/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/yenlikgaisina-ux)

</div>
