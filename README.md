# Chennai Bus Stop Infrastructure & Passenger Experience Audit

## Overview

A data-driven audit of **210 bus stops in Chennai**, focused on understanding passenger experience, accessibility, physical infrastructure, surrounding land use, and recurring problems at bus stops.

The project converts field-audit observations into measurable problem indicators and a **Master Priority Score** that ranks bus stops by observed infrastructure/problem burden.

> **Important:** The priority score is an analytical prioritisation framework, not a prediction of future failures and not a formal engineering safety rating.

---

## Objectives

- Assess the quality of passenger information at bus stops.
- Examine passenger comfort and shelter conditions.
- Evaluate accessibility for pedestrians and wheelchair users.
- Identify road-interface and bus-stop access problems.
- Assess environmental conditions and encroachments.
- Understand the surrounding land use/activity around stops.
- Use qualitative field observations to capture issues that structured fields may miss.
- Create a transparent ranking of bus stops for potential intervention.

---

## Dataset

- **Audited bus stops:** 210
- **Data source:** Chennai bus stop field-audit dataset
- **Data collection context:** Public transport / bus-stop audit
- **Unit of analysis:** Individual bus stop

The analysis uses structured audit responses, derived problem indicators, categorical observations, and qualitative notes/photos where available.

---

## Analysis Workflow

### 1. Passenger Information

Examined whether:

- Bus stop names are clearly displayed.
- Route information is available.
- Information is current, legible, and complete.

### 2. Amenities & Passenger Comfort

Examined shelter, shade, seating, waiting conditions, and other passenger-facing facilities.

### 3. Accessibility & Road Interface

Key accessibility indicators included:

- Pedestrian/wheelchair movement past the stop.
- Wheelchair ramps.
- Tactile paving.
- Bus stopping location.
- Road-space and road-interface problems.
- Kerb and drainage conditions.

### 4. Surrounding Land Use

Bus stops were grouped by nearby activity:

- Commercial
- Mixed Use
- Residential
- Institutional
- Other
- Low Activity / Dead Edge

### 5. Qualitative Observations

Free-text observations were retained to capture issues not fully represented by structured variables.

There were **173 non-null qualitative observations with 123 unique responses**. Examples included poor footpaths, missing shelters, encroachments, poor seating, garbage, and blocked pedestrian movement.

### 6. Master Priority Score

A transparent additive score was created from six problem dimensions:

| Component | Description |
|---|---|
| Shelter | Shelter-related problem score |
| Safety | Safety problem score |
| Road Interface | Road-access / road-space burden |
| Environment | Environmental / encroachment burden |
| Comfort | Seating and passenger-comfort burden |
| Information | Stop-name and route-information problems |

**Master Priority Score = Shelter + Safety + Road Interface + Environment + Comfort + Information**

All component scores were converted to numeric values, with missing values treated as zero for this final ranking calculation.

---

## Final Results

### Priority ranking

Across all 210 audited stops:

- **Mean priority score:** 5.56
- **Median priority score:** 6
- **Minimum:** 1
- **Maximum:** 11
- **Top-25% threshold:** 7
- **High-priority stops:** 69

Four stops reached the maximum observed score of **11**. Two additional stops scored **10**.

The complete ranking is available in:

`master_priority_ranking_all_stops.csv`

---

## Overall Problem Burden

Total accumulated problem points by category:

| Category | Total Problem Points |
|---|---:|
| Road Interface | 305 |
| Environment | 267 |
| Comfort | 248 |
| Information | 225 |
| Shelter | 123 |
| Safety | 0 |

The largest observed burden came from **road-interface problems**, followed by environmental conditions, passenger comfort, and information problems.

The safety score is zero in this particular derived scoring system, so it should **not** be interpreted as meaning that all audited stops are objectively safe. It means the selected safety indicators contributed zero points to this scoring framework.

---

## Accessibility Findings

Several accessibility indicators show substantial infrastructure gaps:

- **73.8%** of audited stops did not allow pedestrians/wheelchair users to move past the bus stop on the footpath without stepping onto the road.
- Only **15.2%** had a wheelchair-access ramp recorded.
- Only **4.8%** had tactile paving recorded.
- **47.6%** of stops were partially encroached.
- **11.4%** were heavily encroached.

These findings indicate that accessibility and pedestrian movement are major areas for infrastructure improvement.

---

## Passenger Information Findings

### Bus stop name

- 38.1% — prominently visible and legible
- 27.6% — name missing
- 20.5% — present but faded, small, or difficult to read
- 13.8% — missing observation

### Route information

- 34.8% — no information displayed
- 27.1% — prominently displayed and appears current
- 17.6% — appears outdated or unreliable
- 6.7% — unclear, faded, or partially missing
- 13.8% — missing observation

Passenger information is therefore not consistently available, legible, or reliable across the audited stops.

---

## Surrounding Land Use

The surrounding activity profile was:

| Land Use Group | Stops | Share |
|---|---:|---:|
| Commercial | 103 | 49.0% |
| Mixed Use | 58 | 27.6% |
| Residential | 26 | 12.4% |
| Institutional | 17 | 8.1% |
| Other | 4 | 1.9% |
| Low Activity / Dead Edge | 2 | 1.0% |

Commercial areas represented the largest share of audited stops.

---

## Key Findings

1. **Road interface is the largest accumulated problem category**, with 305 problem points.
2. **Pedestrian accessibility is a major concern:** 73.8% of stops did not allow users to pass the stop on the footpath without stepping onto the road.
3. **Universal-access infrastructure is limited:** only 15.2% had wheelchair ramps and 4.8% had tactile paving.
4. **Encroachment is widespread:** 59.0% of stops were either partially or heavily encroached.
5. **Passenger information is inconsistent**, with missing, outdated, faded, or unclear stop/route information frequently observed.
6. **Comfort is a substantial part of the overall burden**, ranking third among the accumulated problem categories.
7. **The Master Priority Score provides a transparent way to identify the stops with the highest observed combination of problems.**

---

## Visualisations

The final notebook contains three main visualisations:

### Top 15 Priority Stops

Shows the stops with the highest Master Priority Scores.

![Top 15 Priority Stops](outputs/top_15_priority_stops.png)

### Problem Burden by Category

Compares the total accumulated problem points across the six scoring dimensions.

![Problem Burden by Category](outputs/problem_burden_by_category.png)

### Priority Score Distribution

Shows how the Master Priority Score is distributed across all 210 audited stops.

![Priority Score Distribution](outputs/priority_score_distribution.png)

---

## Repository Structure

Recommended structure:

```text
chennai-bus-stop-audit/
│
├── notebooks/
│   └── chennai_bus_stop_audit.ipynb
│
├── data/
│   └── README.md
│
├── outputs/
│   ├── top_15_priority_stops.png
│   ├── problem_burden_by_category.png
│   └── priority_score_distribution.png
│
├── master_priority_ranking_all_stops.csv
├── high_priority_interventions_top25.csv
├── README.md
└── .gitignore
```

Raw field-audit data should only be committed if its redistribution is permitted. Otherwise, keep the raw dataset local and document how it was obtained.

---

## Methodology Notes

This project is primarily **exploratory data analysis and decision-support**, rather than a machine-learning prediction problem.

A supervised ML model was not used to predict bus-stop problems because the audit does not provide a suitable target variable representing a future outcome. The goal is to **describe observed conditions and prioritise existing problems**, not predict an unknown future label.

The Master Priority Score was therefore kept transparent and interpretable rather than replacing the audit logic with a black-box model.

---

## Limitations

- The audit covers 210 observed stops and may not represent every bus stop in Chennai.
- Some observations contain missing values.
- The priority score depends on the selected indicators and their scoring definitions.
- Additive scores imply equal contribution of component points unless explicitly weighted otherwise.
- The ranking indicates **observed problem burden**, not causal explanations.
- A high score should be treated as a screening/prioritisation signal requiring field verification before infrastructure decisions.

---

## Tools Used

- Python
- Pandas
- NumPy
- Matplotlib
- Jupyter Notebook
- Git / GitHub

---

## Outcome

The project transforms a large field-audit dataset into a concise decision-support workflow:

**Raw audit data → cleaning → problem indicators → topic-level analysis → Master Priority Score → ranked bus stops → visual insights → intervention shortlist**

This makes the analysis useful for communicating infrastructure gaps and identifying bus stops that may deserve further on-ground assessment.

---

## Author

**Pradeep Loganathan**

Data Science Portfolio Project
