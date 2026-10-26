# Data Dictionary

**Source grain:** one row = one DCS operator  
**Records in published sample:** 120  
**Delimiter in CSV:** semicolon (`;`)

| Field             | Type    | Description                                            | Notes                                                                                              |
| ----------------- | ------- | ------------------------------------------------------ | -------------------------------------------------------------------------------------------------- |
| `Operator ID`     | string  | Unique operator identifier                             | Format `OPR-001` … `OPR-120`                                                                       |
| `Operator Name`   | string  | Anonymized display name                                | Real names removed for portfolio                                                                   |
| `Department`      | string  | Work area                                              | 5 values: Fiberline - Digester, Fiberline - Bleaching, Paper Machine, Power Plant, Recovery Boiler |
| `Education Level` | string  | Highest formal education                               | Bachelor (S1), Diploma (D3), High School                                                           |
| `Tenure (Years)`  | integer | Years of service                                       | Used for size encoding and tenure-group banding                                                    |
| `DLP Score`       | integer | Driving license program / theoretical competency score | Range ≈ 60–100. Every 3 years assessment.                                                          |
| `PQS Score`       | integer | Plant Quality / Performance Score                      | Range ≈ 60–100. Operational output metric.                                                         |

## Derived fields (created in Tableau)

| Field                       | Logic                                                                          | Purpose                            |
| --------------------------- | ------------------------------------------------------------------------------ | ---------------------------------- |
| `Quadrant`                  | `IF DLP ≥ p_DLP_threshold AND PQS ≥ p_PQS_threshold THEN "Q1 High Achiever"` … | Core segmentation                  |
| `Tenure Group`              | `≤3 → Junior`, `4–8 → Mid`, `≥9 → Senior`                                      | Box-plot & demographic views       |
| `Performance Gap`           | `PQS Score − DLP Score`                                                        | Department dumbbell & gap analysis |
| `Is Q1` / `Is Q3` / `Is Q4` | Binary 1/0 flags                                                               | KPI card percentages               |
| `Operator Label`            | `Name + " • " + Department + " • " + Tenure + " yr"`                           | Tooltip                            |

## Important caveats (real production data)

The published `raw_data.csv` is a **clean, anonymized sample** created for portfolio reproducibility.

In the original manufacturing environment the data exhibited typical operational messiness:

- Inconsistent department naming (“Fiberline” vs “Fibre Line”)
- Missing PQS records during planned maintenance / downtime (~8%)
- Duplicate rows from mid-year shift reassignments
- A minority of DLP scores older than 2 years (stale competency flags)
- Occasional sensor-error outliers in PQS that required cross-check against maintenance logs

Those issues were handled with a documented CLEAN process (see `docs/issues-log.md` and `docs/methodology.md`). The sample provided here is already cleaned so that anyone can open the workbook and reproduce the quadrant analysis without confidentiality or data-quality friction.
