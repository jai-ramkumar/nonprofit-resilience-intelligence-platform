# Scoring Methodology: Nonprofit Resilience Intelligence Platform

## Overview

This document defines the scoring methodology for Phase 1 of the Nonprofit Resilience Intelligence Platform. It covers the two core concepts being researched and validated in this phase: the Financial Resilience Score and the Capacity Gap Index.

These are research definitions. The formulas and weights will be refined as the data validation progresses.

---

## Financial Resilience Score

### What It Measures

The Financial Resilience Score measures the financial stability and trajectory of a nonprofit organization over time. It is designed to reflect not just where an organization stands today but whether it is becoming more stable or more vulnerable over time.

### Why It Matters

A single year of financial data can be misleading. An organization may look financially healthy in one year but be trending toward stress. This score is designed to capture that trajectory, not just a snapshot.

### Indicators

**Reserve Ratio**
Measures how many months of operating expenses the organization can cover using its net assets. A higher reserve ratio indicates greater financial cushion.

**Revenue Concentration**
Measures how dependent the organization is on a single funding source. High concentration means a single grant reduction could significantly impact operations.

**Operating Margin**
Measures the difference between total revenue and total expenses as a percentage of total revenue. A consistently negative margin is an early stress signal.

**Revenue Growth Trend**
Measures whether total revenue is growing, flat, or declining over a multi-year period.

**Expense Growth Trend**
Measures whether total expenses are growing faster or slower than revenue over the same period. Expenses growing faster than revenue is a warning signal even when margins are still positive.

### Scoring Approach

Each indicator will be calculated from IRS Form 990 data across multiple filing years. Indicators will be normalized and combined using a weighted framework informed by nonprofit financial health literature.

As the research progresses, alternative approaches including data-driven weighting and machine learning methods may be evaluated.

The final score will range from 0 to 100. The score is intended as a comparative and directional indicator rather than a definitive measure of organizational health. A higher score indicates greater financial resilience relative to other organizations in the dataset.

---

## Capacity Gap Index

### What It Measures

The Capacity Gap Index compares the growth in community need against the growth in organizational capacity. It is designed to identify situations where an organization's ability to serve its community is falling behind the demand for its services, even when its financials appear stable.

### Why It Matters

An organization can be financially healthy and still be losing ground. If the community it serves is growing faster than its capacity to respond, that gap is a meaningful risk signal that does not appear in traditional financial reporting.

### Core Formula Concept

```
Capacity Gap Index = Community Need Growth Rate
                     minus
                     Organization Capacity Growth Rate
```

A positive result means community need is growing faster than organizational capacity. This is the stress signal.

A negative result means the organization is keeping pace with or exceeding community need growth.

A result near zero means the organization is broadly in balance with community demand.

### Community Need Growth Rate

Community need growth is part of the long-term Capacity Gap Index vision. Because Phase 1 focuses exclusively on IRS Form 990 data, the Capacity Gap Index will initially be explored using organizational capacity indicators only.

Community-level demand indicators from Census and other public sources will be incorporated and validated in Phase 2.

### Organization Capacity Growth Rate

In Phase 1 this will be approximated using IRS Form 990 fields including total expenses, employee count, and program service revenue as proxies for organizational capacity.

### Important Caveat

The Capacity Gap Index is a research concept at this stage. Phase 1 will focus on whether the concept can be meaningfully measured using public data before any conclusions are drawn about its predictive value.

---

## Explainability

The platform prioritizes interpretability over black-box prediction.

Any future machine learning models will be accompanied by explainability techniques such as SHAP so that users can understand which factors contributed most to a score.

The objective is not only to generate scores but also to provide transparent reasoning behind them. This is especially important in a nonprofit and social sector context where decisions informed by data carry real consequences for the communities being served.

---

## What Is Not Defined Here

The following are part of the long-term platform architecture but are not part of the Phase 1 methodology:

- Stress Signature Classification patterns
- Mission Capacity Forecast model
- Scenario Simulator logic
- AI Executive Advisor prompting framework
- Community Risk Contagion Engine

These will be defined in later phase documentation as the foundational scoring layer is validated.

---

## Next Steps

- Validate indicator availability against ProPublica API response fields
- Cross reference indicators with existing nonprofit financial health literature
- Define normalization approach for each indicator
- Build Silver layer transformations based on this methodology
- Evaluate candidate modeling approaches once the Silver layer and feature engineering process have been validated

---

*This document will be updated as research progresses.*
