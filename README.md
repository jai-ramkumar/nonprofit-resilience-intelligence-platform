# Nonprofit Resilience Intelligence Platform

Predicting nonprofit organizational stress and mission impact from public data.

An independent research and engineering project exploring how public data,
predictive analytics, and scenario simulation can provide early warning of
organizational stress in the nonprofit sector before it becomes a crisis.

---

## The Problem

69% of nonprofits experienced funding cuts in 2025 from at least one source.
46% of nonprofit leaders express concern that their organization may need to
close or merge.
*(Center for Effective Philanthropy, State of Nonprofits 2026)*

Over half of nonprofits have three months or less of cash on hand. 36% ended
2024 with an operating deficit, the highest in ten years of survey data.
*(Nonprofit Finance Fund, State of the Nonprofit Sector 2025)*

Two-thirds of nonprofit leaders report concerns about financial stability, with
the deficit rate nearly doubling from 22% in 2022 to 39% in 2025.
*(Center for Effective Philanthropy, 2026)*

Most existing assessment tools answer historical questions:

- How healthy is this organization today?
- How did it perform last year?
- How does it compare with similar organizations?

They do not answer the questions nonprofit leaders actually need:

- What risks are emerging right now?
- What happens if our largest grant is reduced?
- Can we continue delivering services at current levels?
- Which communities lose services if a major funder exits?

This project focuses on forecasting organizational resilience rather than
measuring historical performance.

---

## What Makes This Different

Most tools that combine IRS Form 990 data with Census indicators measure
current organizational health as a snapshot. This platform measures trajectory.

**Most tools forecast finances. This platform forecasts mission impact.**
Rather than "revenue drops 18%", the output is "1,100 fewer children served
by Q3 2027."

**Most tools assess individual organizations. This platform models ecosystem risk.**
When a major funder exits, the platform maps which communities lose service
coverage and which organizations collapse first.

**Most tools use static Census data. This platform uses leading indicators.**
SNAP enrollment changes, unemployment insurance claims, and eviction filing
rates signal where community need is heading 12 to 18 months before Census
data reflects it.

**Most tools produce scores. This platform produces explanations.**
Every score is traceable to specific data points. The AI advisor layer
translates computed signals into plain language, grounded in model outputs
rather than general knowledge.

**Everything runs on public data only.**
No data sharing agreements. No organizational cooperation required. Any
nonprofit, funder, or researcher can use it for any organization that files
a Form 990.

---

## Current MVP Status

Phase 1 is in active development.

```
Phase 1 - Foundation

  [ ] IRS Form 990 ingestion pipeline (ProPublica API)
  [ ] Bronze Lakehouse layer (raw, append-only)
  [ ] Silver layer - financial feature engineering
  [ ] Capacity Gap Index computation
  [ ] Financial Resilience Score (XGBoost + SHAP)
  [ ] Baseline Power BI dashboard

Phase 2 - Capacity Intelligence                    coming next

  [ ] Community demand layer (Census ACS + leading indicators)
  [ ] Mission Capacity Forecast
  [ ] Scenario Simulator

Phase 3 - Advanced Intelligence                    planned

  [ ] Stress Signature Classification (DTW clustering)
  [ ] AI Executive Advisor
  [ ] Peer cohort outcome matching

Phase 4 - Ecosystem Risk Research                  future research

  [ ] Funder dependency network graph
  [ ] Community Risk Contagion Engine
  [ ] Geographic service coverage gap mapping
```

---

## High-Level Architecture

```
Public Data Sources
IRS 990 · Census ACS · BLS · USASpending · SNAP / UI / Eviction
                        |
                        v
           Bronze - Raw ingestion
           Append-only · Unmodified · Partitioned by source and year
                        |
                        v
           Silver - Feature engineering
           Financial ratios · Capacity Gap Index
           Community indicators · Funder network
                        |
                        v
           Gold - ML models
           XGBoost distress classifier · DTW stress signature clustering
           Prophet capacity forecaster · Graph contagion engine
                        |
                        v
           Mart - Composite scoring
           Resilience Score · Mission Capacity Forecast
           Peer percentiles · Trajectory signature · Network vulnerability
                        |
            +-----------+-----------+
            |           |           |
            v           v           v
       Executive    Scenario    Contagion
       Dashboard    Simulator   Risk Map
                        |
                        v
           AI Executive Advisor
           SHAP-grounded LLM explanations
           Recommended actions · Scenario narration
```

**Platform:** Microsoft Fabric (Lakehouse, Spark notebooks, MLflow, Power BI)

**ML stack:** XGBoost, SHAP, Prophet, DTW k-means, NetworkX

**AI layer:** LLM API with structured prompting grounded in SHAP feature
weights and peer benchmark data

---

## Core Innovations

Detailed methodology is documented in [/docs/methodology.md](docs/methodology.md).

**Capacity Gap Index**

Measures the divergence between community demand growth rate and organizational
revenue growth rate over time. Detects stress trajectories that financial ratios
alone cannot identify. An organization can appear financially stable while demand
is outpacing its capacity to respond.

**Mission Capacity Forecast**

Extracts service volume counts from 990 program description free-text fields
using NLP. Derives cost-per-unit-served from public expense data. Projects
program output forward using financial forecasts. Outputs are expressed in
mission terms: families served, children enrolled, meals delivered.

**Stress Signature Classification**

Applies Dynamic Time Warping k-means clustering to multi-year financial time
series. The model discovers natural trajectory patterns without predefined
labels. Clusters are assigned interpretable names based on shape: Slow Bleed,
Cliff Event, Plateau Trap, Rebound, Boom-Bust, Stable Growth. Each organization
is matched to historical peer cohort outcomes.

**Scenario Simulator**

Accepts user-defined shock parameters including grant reduction, demand surge,
staff turnover, and donor retention change. Recalculates resilience scores,
reserve runway, and mission capacity projections. Operates entirely from public
990 baseline data. No internal organizational data required.

**Community Risk Contagion Engine** *(Phase 4 - Research)*

Constructs a bipartite funding network graph from USASpending grant records and
990 contributor data. Applies betweenness centrality to identify systemically
significant funders. Simulates funder exit events and propagates financial
shocks through the network. Maps service coverage gaps at zip code and county
level.

---

## Data Sources

All data used in this project is publicly available at no cost.

| Source                          | What it provides                                  | Frequency              |
|---------------------------------|---------------------------------------------------|------------------------|
| IRS Form 990 (ProPublica API)   | Revenue, expenses, reserves, program descriptions | Annual (12-18 mo. lag) |
| Census Bureau ACS 5-Year        | Poverty, income, population, housing burden       | Annual                 |
| Bureau of Labor Statistics      | Nonprofit wages, employment, labor tightness      | Monthly / quarterly    |
| USASpending.gov                 | Federal grant awards by recipient EIN             | Continuous             |
| USDA Economic Research Service  | Food insecurity by county                         | Annual                 |
| HUD CHAS                        | Housing affordability and cost burden             | Annual                 |
| USDA FNS SNAP enrollment        | Food assistance enrollment by county              | Monthly                |
| Princeton Eviction Lab          | Eviction filing rates by county                   | Monthly (select geo.)  |

---

## Repository Structure

```
nonprofit-resilience-intelligence-platform/
|
+-- README.md
|
+-- docs/
|   +-- vision.md           Problem framing and sector context
|   +-- architecture.md     Full technical architecture
|   +-- methodology.md      Novel methods: DTW, NLP extraction,
|   |                       contagion engine, SHAP-LLM grounding
|   +-- data_sources.md     Data dictionary, API docs, field mappings
|   +-- mvp_scope.md        Phase 1 scope and acceptance criteria
|   +-- roadmap.md          Full phase-by-phase roadmap with rationale
|
+-- architecture/
|   +-- diagrams/           Architecture diagram exports
|
+-- data/
|   +-- raw/                .gitignored - never committed
|   +-- processed/          .gitignored - never committed
|   +-- sample/             Anonymized sample records for reproducibility
|
+-- notebooks/
|   +-- 01_data_exploration/
|   +-- 02_feature_engineering/
|   +-- 03_model_prototype/
|
+-- src/
|   +-- ingestion/          API connectors: ProPublica, Census, BLS
|   +-- features/           Financial ratio computation, capacity gap
|   +-- models/             Classifier, clustering, forecaster
|   +-- scoring/            Composite score assembly
|
+-- tests/
+-- images/
+-- .gitignore
+-- requirements.txt
+-- CONTRIBUTING.md
```

---

## Roadmap

**Phase 1 - Foundation** *(active)*

Public data ingestion pipelines. Bronze and Silver Lakehouse layers. Financial
feature engineering. XGBoost distress classifier with SHAP. Baseline Power BI
dashboard showing resilience scores for Illinois human services nonprofits.

**Phase 2 - Capacity Intelligence**

Capacity Gap Index. Community demand layer incorporating Census ACS and
high-frequency leading indicators. Mission Capacity Forecast translating
financial projections into program output estimates. Scenario Simulator for
funding shock analysis.

**Phase 3 - Advanced Intelligence**

Stress Signature Classification using DTW time-series clustering. AI Executive
Advisor grounded in SHAP values and peer benchmarks. Peer cohort outcome
matching with survival-style analysis. Full Power BI report suite.

**Phase 4 - Ecosystem Risk Research**

Funder dependency network graph from public grant award data. Community Risk
Contagion Engine modeling service coverage gaps from funding shocks. Geographic
coverage gap mapping at zip code and county level. Open dataset publication.

---

## Methodology Notes

**Why public data only**

This platform is designed to work without any internal organizational data.
Any nonprofit, funder, or researcher can use it for any organization that
files a 990. No data sharing agreements or organizational cooperation required.
This design choice enables broad reproducibility and independent verification.

**Why explainability matters**

Every score in this platform is traceable to specific data points. SHAP values
connect model outputs to individual financial features. The AI advisor layer is
grounded in those computed values. It does not generate explanations from
general knowledge. It translates specific model signals into plain language.

**Limitations**

IRS 990 data carries a 12 to 18 month publication lag. This platform is
designed for strategic planning horizons, not real-time operational monitoring.
Smaller organizations filing 990-EZ or 990-N have reduced data availability.
All projections are probabilistic estimates based on historical patterns and do
not constitute guarantees of future outcomes.

---

## Disclaimer

This is an independent personal research and engineering project. It is not
affiliated with any employer, client, or organization. All data used is
publicly available. This platform is intended for educational, analytical, and
decision-support purposes only. It does not constitute financial, legal, or
investment advice.

---

## Author

**Jai Balaji Ramkumar**
Data Engineer · MS Data Science · Chicago, IL

[LinkedIn](https://www.linkedin.com/in/jaibalaji-ramkumar) ·
[Medium](https://medium.com/@jaibalaji)

---

*Built with public data. Designed for mission-driven decisions.*
