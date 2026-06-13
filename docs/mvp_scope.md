# MVP Scope: Nonprofit Resilience Intelligence Platform

## Overview

Version 1 of the platform establishes the foundational data pipeline and scoring layer using IRS Form 990 data as the sole input source for this phase.

The goal of the MVP is to build a working, end-to-end proof of concept that produces two core outputs:

- Financial Resilience Score
- Capacity Gap Index Score

This MVP is intentionally limited in scope so the project remains realistic, testable, and achievable as a solo engineering effort.

---

## MVP Version 1

### Input

- IRS Form 990 data via the ProPublica Nonprofit Explorer API

### Outputs

- Financial Resilience Score
- Capacity Gap Index Score
- Baseline Power BI dashboard

---

## What Is Not Included in the MVP

The following capabilities are part of the long-term architecture but are explicitly deferred to later phases:

- AI Executive Advisor or natural language interface
- Scenario Simulator
- Community Risk Contagion Engine
- Census demographic data integration
- BLS labor market data integration
- Mission Capacity Forecast
- Stress Signature Classification

These are excluded from the MVP to keep the first version focused on validating the foundational data pipeline and scoring logic.

---

## Phase 1 Checklist

- [ ] ProPublica API ingestion into Bronze layer
- [ ] Bronze layer notebook for raw IRS Form 990 data
- [ ] Silver layer notebook for financial ratio calculations
- [ ] Capacity Gap Index scoring logic
- [ ] Financial Resilience Score using XGBoost and SHAP explainability
- [ ] Baseline Power BI dashboard for score visualization

---

## Success Criteria

The MVP is complete when:

- Real IRS Form 990 data is ingested from the ProPublica API and stored in the Bronze layer
- Financial features are calculated in the Silver layer
- Capacity Gap Index Score is generated
- Financial Resilience Score is generated
- SHAP explanations are available for model outputs
- A Power BI dashboard displays scores from processed 990 data

---

## MVP Design Principle

The MVP is designed to answer one core question:

> Can publicly available IRS Form 990 data be transformed into a useful early indicator of nonprofit organizational resilience?

Later phases will expand the platform with community demand indicators, mission impact forecasting, scenario simulation, and ecosystem level risk modeling.
