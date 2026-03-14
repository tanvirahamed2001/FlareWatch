# FlareWatch
Alberta Operator Emissions Benchmarking & Regulatory Risk Scorer

# 🔥 FlareWatch
### Alberta Operator Emissions Benchmarking & Regulatory Risk Intelligence Platform

[![Databricks](https://img.shields.io/badge/Built%20on-Databricks-FF3621?style=flat-square&logo=databricks&logoColor=white)](https://databricks.com)
[![Delta Lake](https://img.shields.io/badge/Delta-Lake-00ADD8?style=flat-square&logo=apachespark&logoColor=white)](https://delta.io)
[![Apache Spark](https://img.shields.io/badge/Apache-Spark-E25A1C?style=flat-square&logo=apachespark&logoColor=white)](https://spark.apache.org)
[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

> **Built at the Calgary Databricks Hackathon — March 26, 2026**  
> Real Petrinex data. Real Alberta operators. Real regulatory risk.

---

## 🧠 The Problem

Alberta oil and gas operators have **no real-time visibility** into which facilities are approaching AER (Alberta Energy Regulator) emissions limits — exposing them to:

- 💸 **Fines exceeding $500,000** for regulatory violations
- 🛑 **Forced shutdowns** costing $100K–$500K per day
- 📉 **ESG investor pressure** from undetected high-intensity flaring

Regulators lack a unified view. Operators fly blind. FlareWatch changes that.

---

## 💡 The Solution

FlareWatch is an **emissions intelligence platform** built on Databricks that:

1. **Benchmarks** every Alberta operator by flare intensity (emissions per barrel)
2. **Scores** facilities by regulatory risk — 🔴 HIGH / 🟡 MEDIUM / 🟢 LOW
3. **Correlates** emissions behaviour with WTI oil price movements
4. **Ranks** regions by total emissions volume
5. **Enables** natural language queries over real Petrinex data via Genie AI

---

## 📊 Data Sources

All data is real — sourced from **Alberta Petrinex** (2024–2025):

| Table | Rows | Description |
|-------|------|-------------|
| `volumetrics` | 27M | Production volumes by facility |
| `facility_emissions` | 400K | Flare & vent volumes per facility |
| `facilities` | 30K | Facility metadata & region |
| `operators` | 600 | Operator registry |
| `wells` | 100K | Well-level data |
| `ngl_volumes` | 2.5M | Natural gas liquids |
| `market_prices` | 14 | WTI, WCS, AECO monthly prices |
| `field_codes` | 80 | Field classification codes |

All tables loaded into: `hackathon.energy_data` catalog on Databricks.

---

## 🏗️ Architecture

```
Raw Petrinex Data (hackathon.energy_data)
        │
        ▼
┌─────────────────────────────────────────┐
│     02_flarewatch_emissions_analysis    │ 
│   • Flare intensity per operator        │
│   • Regulatory risk scoring 🔴🟡🟢     │
│   • WTI price vs emissions correlation  │
│   • Regional emissions summary          │
└─────────────────────────────────────────┘
        │
        ▼
┌─────────────────────────────────────────┐
│         FlareWatch Delta Tables         │
│  flarewatch_operator_scores             │
│  flarewatch_risk_scores                 │
│  flarewatch_price_correlation           │
│  flarewatch_regional_summary            │
│  emissions_intensity (team)             │
└─────────────────────────────────────────┘
        │
        ├──► 📊 Databricks Dashboard
        │        • Flare Intensity Bar Chart
        │        • Risk Score Table
        │        • Price vs Emissions Line Chart
        │        • Regional Emissions Map
        │
        └──► 🤖 Genie AI Space
                 • Natural language queries
                 • "Which operator has the highest flare intensity?"
                 • "Show HIGH RISK facilities in Peace Country"
```

---

## 📁 Notebooks

| Notebook | Description |
|----------|-------------|
| `02_flarewatch_emissions_analysis` | Core analysis — flare intensity, risk scoring, price correlation, regional breakdown |
| `03_risk_scorer` | Facility-level risk scoring engine |

---

## 🔑 Key Findings

### 1. Flare Intensity Leaders
**DEL CANADA GP LTD.** leads all operators with a flare intensity score of **3,756** — over 3× the #2 operator BEARSPAW PETROLEUM at **3,623**.

### 2. Extreme Facility Outlier
**TAMARACK VALLEY ENERGY LTD.** facility `ABBT0161372` in Peace Country recorded an emissions intensity of **1.99** — nearly 2 units of emissions per barrel produced, the highest single-facility reading in the dataset.

### 3. Price vs Emissions — The Key Insight
Analysis of 12 months of Petrinex data shows Alberta operators **maintain consistent flaring levels regardless of oil price**:

| Month | WTI (USD/bbl) | Total Emissions |
|-------|--------------|-----------------|
| May 2025 | $61.73 (lowest) | 143,160 |
| July 2025 | $74.82 (highest) | 133,484 |

> Emissions are driven by **operational necessity**, not profit margins — making regulatory monitoring essential regardless of market conditions.

### 4. Regional Hotspots
Peace Country and Central Alberta account for the highest absolute flaring volumes, while Southeast Alberta has the most facilities operating near regulatory thresholds.

---

## 🤖 Genie AI Assistant

FlareWatch includes a **natural language interface** powered by Databricks Genie over all 8 source tables + FlareWatch analytics tables.

Example queries:
- *"Which operator has the highest flare intensity?"*
- *"Show me all HIGH RISK facilities in the Montney formation"*
- *"How did emissions change when WTI dropped below $65?"*
- *"Compare Peace Country vs Central Alberta total flaring in 2025"*

---

## 🚀 Getting Started

### Prerequisites
- Databricks workspace with Unity Catalog
- Access to `hackathon.energy_data` catalog
- Serverless SQL warehouse

### Run the Analysis
1. Clone this repo into your Databricks workspace via **Repos**
2. Open `02_flarewatch_emissions_analysis`
3. Run all cells — outputs saved to `hackathon.energy_data` as Delta tables
4. Open the **FlareWatch Dashboard** for visualizations
5. Open **Genie → FlareWatch AI Assistant** for natural language queries

---

## 👥 Team

Built in one day at the **Calgary Databricks Hackathon, March 26, 2026**

| Name | Contribution |
|------|-------------|
| Tanvir Ahamed | Emissions analysis, risk scoring, price correlation, regional breakdown |
| Tejbal | Emissions intensity table, facility-level analysis |
| Team | Dashboard, Genie Space, pitch deck |

---

## 🏆 Hackathon

**Calgary Databricks Hackathon — March 26, 2026**  
Theme: Energy Intelligence on the Lakehouse  
Dataset: Real Alberta Petrinex data (27M+ rows)

---

*FlareWatch — because every flare tells a story regulators need to hear.*
