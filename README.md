# Building Energy Anomaly Detection
### Identifying Inefficient Buildings for Retrofit Prioritisation

![Python](https://img.shields.io/badge/Python-3.10-blue) ![Status](https://img.shields.io/badge/Status-Complete-green) ![Data](https://img.shields.io/badge/Data-UK%20EPC%20Open%20Data-orange)

---

## Business Question

> **Which residential buildings in England and Wales are anomalously energy-inefficient, and how can local authorities and retrofit programmes prioritise them for intervention?**
>
> The UK government has committed to improving the energy efficiency of homes to meet net-zero targets. With millions of EPC (Energy Performance Certificate) records publicly available, this project applies anomaly detection techniques to identify buildings that fall outside expected efficiency patterns — flagging them as priority candidates for retrofit investment.
>
> ---
>
> ## Dataset
>
> **Source:** [UK Government EPC Open Data](https://epc.opendatacommunities.org/) — Ministry of Housing, Communities & Local Government
> **Coverage:** England and Wales, domestic properties
> **Key features used:**
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
> ## Approach
>
> This project uses two complementary anomaly detection methods:
>
> **1. IQR (Interquartile Range) — Statistical Method**
> Applied per feature to identify extreme outliers. A building is flagged as anomalous when multiple features simultaneously fall outside the IQR bounds — calibrated to capture 1–5% of records.
>
> **2. Isolation Forest — Machine Learning Method**
> An unsupervised ensemble method that isolates anomalies by randomly partitioning the feature space. Buildings that require fewer splits to isolate are more likely to be anomalies. PCA visualisation in 2D is used to assess separation of anomalous vs normal records.
>
> Both methods were chosen because they work well on unlabelled data (no pre-defined "bad building" labels exist), which is typical in real-world sustainability datasets.
>
> ---
>
> ## Key Findings
>
> - Approximately **2.3% of properties** were flagged as anomalous by both methods combined
> - - Anomalous buildings showed **energy consumption 3–5x higher** than the dataset median
>   - - The highest concentration of anomalies was found in properties built **pre-1930**, with solid wall construction and no insulation recorded
>     - - CO2 emissions in flagged properties averaged **4.1 tonnes/year** vs 1.8 tonnes for normal properties
>       - - Isolation Forest and IQR agreed on **~78%** of flagged cases, providing high-confidence candidates for intervention
>        
>         - ---
>
> ## What a Business Would Do With This
>
> A local authority or housing association could:
> 1. Cross-reference flagged properties against owner/tenure data to identify eligible households for government retrofit schemes (e.g. ECO4, Great British Insulation Scheme)
> 2. 2. Prioritise outreach and surveying to properties in the top anomaly confidence tier
>    3. 3. Estimate potential CO2 reduction per intervention using the predicted efficiency gap
>       4. 4. Report impact metrics to central government funding bodies
>         
>          5. ---
>         
>          6. ## Repository Structure
>         
>          7. ```
> building-energy-anomaly-detection/
> │
> ├── notebook/
> │   └── building_energy_anomaly_detection.ipynb   # Full analysis notebook
> │
> ├── data/
> │   └── README.md                                  # Data source instructions
> │
> ├── outputs/
> │   └── figures/                                   # Saved visualisations
> │
> └── README.md
> ```
>
> ---
>
> ## Skills Demonstrated
>
> `Python` `Pandas` `NumPy` `Scikit-learn` `Matplotlib` `Seaborn` `IQR` `Isolation Forest` `PCA` `EDA` `Anomaly Detection` `Open Government Data`
>
> ---
>
> ## Author
>
> **Yenlik Gaisina, MPH**
> Data Analyst | Cambridge Data Science & AI
> [LinkedIn](https://www.linkedin.com/in/yenlik-gaisina/) | [GitHub](https://github.com/yenlikgaisina-ux)
