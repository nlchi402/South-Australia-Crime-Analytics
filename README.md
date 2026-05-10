# South Australia Crime Analytics Report

## Overview

This Power BI report analyses crime patterns in South Australia across three perspectives:

1. **Crime type differences** between offences against property and offences against the person  
2. **The impact of COVID-19** on crime rates before, during, and after the pandemic period  
3. **Postcode-level socioeconomic patterns** in crime rates using unemployment, youth population share, and median weekly income  

The report combines South Australian crime data with 2021 Census-based postcode indicators to explore both temporal and geographic patterns in crime.

## Tools Used

- **Power BI** – dashboard development and interactive reporting  
- **Power Query** – data cleaning and transformation  
- **DAX** – measures for offence counts, crime rates, percentage change, and socioeconomic indicators  
- **Geospatial mapping** – postcode-level crime analysis  

---

## Report Pages

### 1. Crime Type Differences – Property vs Person

This page compares offences against property with offences against the person for the period **July 2024 to June 2025**.

It includes:

- Total offence count  
- Share of property vs person offences  
- Monthly crime rates per 1,000 residents  
- Geographic distribution of total offences by postcode  
- Top Level 2 offence categories

![Crime Type Differences](images/page1-crime-type-differences.png)

---

### 2. COVID-19 Impact on Crime

This page compares crime patterns across three periods:

- **Pre-COVID:** July 2017 – February 2020  
- **COVID:** March 2020 – January 2022  
- **Post-COVID:** February 2022 – June 2025  

It includes:

- Average monthly crime rate by period  
- COVID vs Pre-COVID percentage change by postcode  
- Top 5 postcodes with the largest absolute change in crime rate  
- Monthly offence counts from 2017 to 2025 with COVID start and end markers

![COVID-19 Impact](images/page2-covid-impact.png)

---

### 3. Crime Rate and Socioeconomic Patterns

This page explores how annualised crime rates vary across South Australian postcodes by selected socioeconomic indicators.

It includes:

- Crime rate vs unemployment rate  
- Crime rate vs youth population share  
- Postcode map showing crime rate and estimated unemployed population  
- Heatmap of crime rate by youth share and median weekly income band  

The page is exploratory and shows **associations rather than causal relationships**.

![Socioeconomic Patterns](images/page3-socioeconomic-patterns.png)

---

## Key Questions Explored

- How do **property offences** and **person offences** differ in scale and trend?
- Did crime rates change during the COVID-19 period compared with pre-COVID levels?
- Which postcodes experienced the largest changes in crime rate during COVID?
- How do postcode-level crime rates vary with:
  - unemployment rate,
  - youth population share,
  - median weekly personal income?

---

## Data Model

The report uses a postcode-level data model centred on **2021 Census postcode data**, linked to crime fact tables and supporting Census tables for labour force status, income, and demographic indicators.

Key components include:

- Crime data for **2016–2025**
- A dedicated **date dimension**
- Postcode-level 2021 Census tables
- Supporting tables for:
  - labour force status,
  - selected medians and averages,
  - youth population,
  - postcode-level offence summaries

---

## Data Preparation and Analytical Approach

### Data preparation

The project involved:

- Cleaning and transforming offence datasets in **Power Query**
- Standardising date and postcode fields
- Building a date dimension for time-series analysis
- Creating postcode-level joins between crime data and Census indicators
- Developing DAX measures for:
  - offence counts,
  - property/person offence shares,
  - crime rates per 1,000 residents,
  - pre-COVID / COVID / post-COVID rates,
  - percentage change in crime rate,
  - youth share,
  - unemployment rate,
  - median weekly personal income  

### Selected DAX measures

The report includes measures for:

- `Offences`
- `Offences — Property`
- `Offences — Person`
- `% property`
- `% person`
- `Rate per 1k`
- `Rate/1k per month (pre)`
- `Rate/1k per month (covid)`
- `Rate/1k per month (post)`
- `Δ% rate (covid vs pre)`
- `Abs Δ%`
- `Unemployment rate`
- `Youth share (total)`
- `Median personal income (weekly)`

---

## Methodological Decisions and Limitations

### 1. Use of rates rather than raw counts

Raw offence counts can be misleading when comparing postcodes with very different population sizes.  
For cross-postcode comparisons, the report uses **crime rate per 1,000 residents** to improve comparability.

### 2. Excluding small-population postcodes

Postcodes with fewer than **2,000 residents** were excluded from rate-based socioeconomic analysis because small denominators can produce unstable or inflated crime rates.

### 3. Treatment of Adelaide CBD

**Adelaide CBD (postcode 5000)** was excluded from the socioeconomic pattern analysis.  
The CBD has a much larger daytime and visitor population than its resident population, so per-resident crime rates may not be directly comparable with typical residential postcodes. Including it could disproportionately influence the relationship between crime rate and socioeconomic indicators.

### 4. Association does not imply causation

The socioeconomic analysis is exploratory.  
Observed relationships between crime rate, unemployment, youth share, and income should be interpreted as **associations**, not evidence of causal effects.

---

## Key Insights

- Offences against property made up approximately **75%** of total offences in the selected 12-month period, while offences against the person accounted for about **25%**.
- Average monthly crime rate was lower during the COVID period than in the pre-COVID period.
- Crime patterns varied across postcodes, with a small number of areas showing the largest absolute changes during COVID.
- Higher crime-rate postcodes appeared to be associated with higher unemployment and higher youth population share, although these relationships are descriptive rather than causal.

---

## Repository Contents

```text
South-Australia-Crime-Analytics/
│
├── South_Australia_Crime_Analytics.pbix
├── README.md
├── images/
│   ├── page1-crime-type-differences.png
│   ├── page2-covid-impact.png
│   ├── page3-socioeconomic-patterns.png
│   └── data-model.png
└── data/
    └── [optional public datasets or data dictionary]
