# DCS Operator Performance Diagnostics  
**Workforce Skill & Performance Analytics · DLP vs PQS Quadrant Framework**

[![Tableau Public](https://img.shields.io/badge/Tableau_Public-View_Dashboard-blue?logo=tableau)](https://public.tableau.com/app/profile/anderson.rumuy/viz/Operators_17767371215810/Dashboard)
[![Portfolio Write-up](https://img.shields.io/badge/Portfolio-HTML_Case_Study-teal)](docs/portfolio.html)

> Who can we promote, who needs retraining, and where is our training budget being wasted?

**Context:** Pulp & Paper Mill · Southeast Asia (West Papua) · 120 DCS operators · 5 departments

---

## Overview

This project bridges the gap between theoretical competency assessments (**DLP** – Digital Learning Platform scores) and real-world operational output (**PQS** – Plant Quality / Performance Scores) for Distributed Control System operators in a continuous-process manufacturing environment.

Traditional HR and Operations systems treated these metrics in isolation. The result: promotions based on exam performance that did not translate to plant-floor results, and high-performing operators overlooked because of lower test scores.

The solution is a **parametric quadrant framework** that classifies every operator into one of four actionable profiles and surfaces the corresponding HR / L&D / Operations interventions.

### Live Dashboard
**[→ Open interactive Tableau dashboard](https://public.tableau.com/app/profile/anderson.rumuy/viz/Operators_17767371215810/Dashboard)**

![Final Dashboard](images/dashboard-final.png)

---

## Key Results (at default thresholds: DLP ≥ 82.5 · PQS ≥ 90)

| Quadrant | Operators | % | Profile | Primary Action |
|----------|-----------|---|---------|----------------|
| **Q1 High Achiever** | 29 | 24.2% | High DLP + High PQS | Fast-track promotion / competency-based pay / peer mentors |
| **Q2 Test Review** | 24 | 20.0% | Low DLP + High PQS | Revise assessment format (oral / observational) – capture tacit knowledge |
| **Q3 Training Transfer** | 43 | 35.8% | High DLP + Low PQS | Root-cause analysis (curriculum, trainer, equipment) |
| **Q4 Retrain** | 24 | 20.0% | Low DLP + Low PQS | Remove from critical DCS duties + structured improvement plan |

**Supporting views**
- Department gap (dumbbell chart) – Recovery Boiler shows largest positive PQS–DLP gap
- Tenure distribution (box plots)
- Quadrant mix by education level (Bachelor correlates with higher DLP but not necessarily higher PQS)

---

## Methodology

### READY Framework
- **R**epresentative data from actual manufacturing HR + DCS logs (not a public Kaggle set)
- **E**xec-driven questions scoped with HR Director / L&D / Plant Operations stakeholders first
- **A**nalytical frameworks: quadrant segmentation + Kirkpatrick-inspired training transfer lens
- **D**ata best practices: FIXED LOD expressions, dynamic parameters, documented grain
- **Y**our insights mapped to named stakeholder levers (compensation, succession, safety)

### CLEAN Data Preparation
Five-stage process with a full Issues Log:
1. Conceptualize (grain = one operator)
2. Locate (department naming variants, shift-reassignment duplicates)
3. Evaluate (8.3% missing PQS → excluded as downtime; no imputation)
4. Augment (tenure bands, performance gap, stale-score flags)
5. Note (every decision logged)

See `docs/issues-log.md` and `docs/methodology.md` for details.

---

## Dashboard Features

- **Parametric thresholds** – Drag `p_DLP_threshold` and `p_PQS_threshold` to instantly re-draw quadrants
- **Size encoding** – Bubble size = tenure
- **Color** – Quadrant membership
- **Tooltips** – Operator label, department, tenure, gap
- Supporting charts for department gaps, tenure distribution, and education mix

---

## Repository Structure

```text
├── dashboard/          Tableau workbook (.twb)
├── images/             High-resolution screenshots
├── data/               Sample data + data dictionary
├── docs/               Full portfolio case study (HTML) + methodology notes
└── sql/                (Optional) preparation queries