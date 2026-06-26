# Data Dictionary: Nonprofit Resilience Intelligence Platform

## Overview

This document defines the data fields used in Phase 1 of the Nonprofit Resilience Intelligence Platform. All fields in this phase are sourced exclusively from IRS Form 990 filings via the ProPublica Nonprofit Explorer API.

---

## Source Reference

| Source | Description |
|---|---|
| IRS Form 990 (ProPublica Nonprofit Explorer API) | Annual information return filed by U.S. tax-exempt nonprofit organizations. Used as the sole data source for Phase 1. |

---

## Field Definitions

| Source | Field Name | Description | Used In |
|---|---|---|---|
| IRS Form 990 | Total Revenue | Total income received by the organization during the fiscal year from all sources including contributions, grants, program services, and investments. | Financial Resilience Score |
| IRS Form 990 | Total Expenses | Total amount spent by the organization during the fiscal year across all activities including programs, administration, and fundraising. | Financial Resilience Score |
| IRS Form 990 | Total Assets | The total value of everything the organization owns including cash, investments, property, and equipment at the end of the fiscal year. | Financial Resilience Score, Capacity Gap Index |
| IRS Form 990 | Total Liabilities | The total amount the organization owes to outside parties including loans, accounts payable, and deferred revenue at the end of the fiscal year. | Financial Resilience Score |
| IRS Form 990 | Net Assets | The difference between total assets and total liabilities. Represents the organization's financial cushion or equity. Used to calculate the reserve ratio. | Financial Resilience Score |
| IRS Form 990 | Total Contributions | Total donations and gifts received from individuals, foundations, and corporations during the fiscal year. Excludes government grants. | Financial Resilience Score |
| IRS Form 990 | Government Grants | Grants and contracts received from federal, state, and local government sources during the fiscal year. Tracked separately from private contributions to assess government funding dependency. | Financial Resilience Score |
| IRS Form 990 | Employee Count | Total number of employees reported by the organization. Used as a proxy for organizational capacity and workforce size. Direct measures of service capacity are not consistently available in public IRS Form 990 filings, so this field serves as the closest available approximation. | Capacity Gap Index |
| IRS Form 990 | Program Expenses | Total expenses spent directly on the organization's mission-driven programs and services. Commonly used as an indicator of mission investment. | Financial Resilience Score, Capacity Gap Index |
| IRS Form 990 | Program Service Revenue | Revenue earned directly from delivering program services such as fees, tuition, or contracts. Distinct from donations and grants. Used to assess earned income diversification. | Financial Resilience Score |

---

## Derived Fields

These fields are not pulled directly from the API. They are calculated during the Silver layer transformation from the raw fields above.

| Field Name | Formula | Used In |
|---|---|---|
| Reserve Ratio | Net Assets divided by (Total Expenses divided by 12) | Financial Resilience Score |
| Operating Margin | (Total Revenue minus Total Expenses) divided by Total Revenue | Financial Resilience Score |
| Government Funding Dependency | Government Grants divided by Total Revenue | Financial Resilience Score |
| Revenue Growth Rate | Year over year percentage change in Total Revenue | Financial Resilience Score |
| Expense Growth Rate | Year over year percentage change in Total Expenses | Financial Resilience Score |
| Capacity Growth Rate | A composite measure derived from year over year changes in Program Expenses and Employee Count. The final methodology will be refined during model development. | Capacity Gap Index |

---

## Data Quality Considerations

Public Form 990 data may contain reporting delays, amended filings, or variations across organizations. Phase 1 focuses on establishing a consistent and reproducible data preparation process before evaluating predictive performance.

---

## Notes

- All raw fields are sourced from IRS Form 990 filings obtained through the ProPublica Nonprofit Explorer API. Where available, multiple filing years will be retrieved for each organization to support trend-based calculations.
- Fields may vary slightly across filing types (Form 990, 990-EZ, 990-PF). Phase 1 will focus on standard Form 990 filers only.
- A more complete Funding Concentration Index covering all revenue source types will be introduced in Phase 2.
- Census and BLS fields are deferred to Phase 2 and are not included in this document.

---

*This document will be updated as additional fields are identified during ProPublica API validation.*
