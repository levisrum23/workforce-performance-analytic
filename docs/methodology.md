# Methodology (short)

## 1. Problem framing (READY – Exec-driven)

Three stakeholder questions were fixed **before** any analysis:

1. **HR Director** – Who should be fast-tracked for promotion / competency-based pay, and who needs a structured improvement plan?
2. **L&D Manager** – Where is training investment failing to translate into plant-floor performance?
3. **Plant Operations** – Are any operators currently on critical DCS duties while showing both low knowledge and low output (safety / production risk)?

## 2. Data preparation (CLEAN)

| Stage | What was done |
|-------|---------------|
| **C**onceptualize | Grain = one operator. Metrics = annual DLP + aggregated PQS. |
| **L**ocate | Department naming variants, 14 shift-reassignment duplicates. |
| **E**valuate | ~8% missing PQS → excluded (downtime), not imputed. |
| **A**ugment | Tenure bands, Performance Gap, stale-score flag. |
| **N**ote | Every decision logged in the Issues Log. |

## 3. Analytical framework

A simple 2×2 matrix with **dynamic parameters**:

- X-axis → DLP Score (theoretical)
- Y-axis → PQS Score (operational)
- Thresholds controlled by Tableau parameters so stakeholders can test “what if we raise the bar?”

Four resulting profiles map directly to interventions (promote, revise assessment, investigate training transfer, retrain / remove from critical duties).

## 4. Design principles

- KPI cards answer the three exec questions in < 10 seconds.
- Scatter + parameters let the HR Director explore sensitivity.
- Supporting charts (department gap, tenure, education) provide context without cluttering the primary decision view.
- All cleaning decisions are documented so the analysis can be defended in stakeholder meetings.