# Vision

## The Problem

Most nonprofit organizations do not see financial or operational stress coming
until it is too late.

They are focused on delivering services every day. By the time warning signs
appear in annual reports, the damage is already done. Staff have left. Programs
have been cut. Families have lost access to services they depend on.

The tools that exist today answer only one question:
how healthy is this organization right now?

They do not answer the question that matters most:
what is coming next?

A nonprofit can show healthy finances today while demand in their community is
growing three times faster than their funding. A nonprofit can look stable on
paper while quietly losing staff at a rate that will collapse service delivery
within a year. A nonprofit can be one government grant away from crisis and
have no analytical framework to see it coming.

Existing tools primarily focus on historical performance and financial health.
Few publicly available platforms focus on forecasting organizational stress and
mission impact using only public data.

This project is an attempt to address that gap.

---

## The Opportunity

The IRS requires every nonprofit to file a Form 990 annually. This filing
contains revenue, expenses, reserves, staffing levels, and program descriptions.
Over 1.8 million filings are publicly available going back more than a decade.

The US Census Bureau publishes annual data on poverty, income, population
growth, and housing burden at the county and zip code level.

The Bureau of Labor Statistics publishes wage and employment trends for social
service workers by region.

Federal grant award data is publicly available through USASpending.gov.

Few platforms have combined these sources into a single forward-looking
intelligence system designed specifically for nonprofit decision makers. This
project explores whether that combination can produce meaningful early warning
signals.

---

## Core Research Hypothesis

Most nonprofit distress models focus on the organization in isolation.

This project explores a different hypothesis:

Organizational stress emerges when community demand grows faster than
organizational capacity to respond.

The Capacity Gap Index measures that divergence.

```
Community Need Growth Rate
        minus
Organization Capacity Growth Rate
        equals
Capacity Gap Index
```

The larger and more persistent the gap becomes, the greater the likelihood
that organizational stress will emerge, even when traditional financial ratios
appear healthy.

This hypothesis is the conceptual foundation of the platform. If validated,
it represents a meaningful contribution to how nonprofit resilience is measured
and forecasted.

---

Traditional nonprofit risk models focus primarily on internal financial
indicators such as revenue growth, reserve levels, and operating margins.

This project explores the idea that organizational stress may emerge earlier
through a mismatch between external demand and internal capacity.

An organization may appear financially stable while community demand grows
significantly faster than its ability to respond.

If this hypothesis is correct, the Capacity Gap Index may provide an earlier
warning signal than traditional financial ratios alone.

Testing this hypothesis is one of the primary objectives of this project.

This will be explored using publicly available IRS Form 990 financial data
combined with Census Bureau community demand indicators, allowing the hypothesis
to be tested across a large and diverse sample of nonprofit organizations
without requiring internal organizational data.

---

## The Vision

Build an open, explainable platform that uses only public data to help nonprofit
leaders answer questions they cannot currently answer:

- Is our organization keeping pace with the demand we were built to serve?
- What happens to our capacity if we lose our largest grant?
- How many fewer families will we serve if funding stays flat and costs keep
  rising?
- Are we following a pattern that has historically led to organizational
  collapse?

The platform is not intended to replace human judgment. It is designed to
inform it.

It is designed to give a nonprofit CEO, a program director, or a board member
a clearer picture of where their organization is heading so they can act before
a crisis arrives rather than after.

---

## What This Platform Is Designed To Do

**Score organizational resilience.**
A composite score built from financial health, operational capacity relative
to community demand, and external risk indicators. Not just how healthy an
organization is today but whether it is moving toward stability or away from it.

**Forecast mission impact in human terms.**
Not revenue projections. Program projections. How many children served. How
many families supported. How many meals delivered. Financial decline translated
into the language of mission.

**Recognize trajectory patterns.**
Organizations in stress tend to follow recognizable paths. A slow multi-year
erosion. A sudden collapse after one grant ends. Flat revenue while costs keep
rising. The platform is designed to identify which pattern an organization is
following and show what happened to similar organizations that followed the
same path historically.

**Simulate decisions before they are made.**
What happens to our resilience score if we lose our largest government grant?
What if community demand grows faster than our funding? The scenario simulator
is designed to let leaders explore these questions before committing to a
course of action.

---

## Who Benefits

**Nonprofit executives and boards**
Leaders who need to make strategic decisions about program expansion, hiring,
and grant applications. This platform is designed to give them a forward-looking
analytical foundation they do not currently have.

**Program directors and research teams**
Staff responsible for understanding community need and organizational capacity.
This platform is designed to automate analysis that currently takes weeks of
manual work.

**Funders and philanthropic organizations**
Foundations and government agencies that want to understand which organizations
in their portfolio are under stress and which communities are most at risk if
funding is reduced.

**Researchers and policy advocates**
Academics and policy professionals studying the nonprofit sector, organizational
resilience, and the relationship between public funding decisions and community
service availability.

---

## What Makes This Different

Existing tools measure current health. This platform is designed to measure
trajectory.

Existing tools speak the language of finance. This platform is designed to
speak the language of mission.

Existing tools look at one organization at a time. This platform is designed
to look at the organization in the context of its community.

Existing tools require internal organizational data. This platform is designed
to run entirely on publicly available data. Any organization, funder, or
researcher can use it for any nonprofit that files a Form 990, with no data
sharing agreements and no organizational cooperation required.

---

## Guiding Principles

**Public data only.**
Every data source used in this platform is freely and publicly available. The
methodology is transparent and independently reproducible.

**Explainability over accuracy.**
A score that a nonprofit leader can understand and act on is more valuable than
a score that is marginally more accurate but impossible to interpret. Every
output in this platform is designed to be traceable to specific data inputs.

**Mission language over financial language.**
The goal of a nonprofit is not to maximize revenue. It is to deliver services
to people who need them. Every metric in this platform is designed with that
distinction in mind.

**Forward-looking over backward-looking.**
Historical performance is context. It is not strategy. This platform is
designed to support decisions about what comes next, not explanations of what
already happened.

---

## Research Questions

This project is currently exploring the following questions:

1. Can public nonprofit data be used to identify early signals of organizational
   stress before they appear in annual reports?

2. Does the gap between community demand growth and organizational capacity
   growth provide predictive value beyond traditional financial ratios?

3. Can mission impact be forecast in program terms using publicly available
   financial and program information?

4. Can explainable models provide nonprofit leaders with actionable early
   warning indicators that are interpretable without data science expertise?

These questions will guide the development, methodology, and evaluation of
the platform.

---

## Current Status

This project is in the research and architecture phase.

Phase 1 development is focused on building the data ingestion pipeline for
IRS Form 990 data, engineering the core financial features, and producing a
baseline resilience score for Illinois human services nonprofits.

Subsequent phases will add community demand forecasting, mission capacity
projection, scenario simulation, and advanced research into ecosystem-level
risk modeling.

---

*This is an independent personal research and engineering project. It is not
affiliated with any employer or organization. All data used is publicly
available. This platform is intended for educational, analytical, and
decision-support purposes only.*
