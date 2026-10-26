# Dashboard – Tableau Workbook

## Files

| File                         | Description                |
| ---------------------------- | -------------------------- |
| `workforce performance.twbx` | Packaged Tableau workbook  |

## How to open

1. Download the workbook.
2. Open with **Tableau Desktop** or **Tableau Public**.
3. The two key parameters appear on the right of the Performance Matrix:
   - `p_DLP_threshold` (default **82.5**)
   - `p_PQS_threshold` (default **90.0**)
4. Drag the sliders to re-draw the four quadrants instantly.

## Calculated fields (key ones)

- **Quadrant** – classifies each operator into Q1–Q4 using the two parameter thresholds.
- **Tenure Group** – Junior (0-3), Mid (4-8), Senior (9+).
- **Performance Gap** – `PQS Score − DLP Score`.
- **Is Q1 / Is Q3 / Is Q4** – binary flags used for percentage KPI cards.
- **Operator Label** – tooltip helper: `Name • Department • Tenure yr`.

## Design notes

- Bubble **size** = tenure (years).
- Bubble **color** = quadrant membership (green / yellow / orange / red).
- Reference lines are driven by the parameters so the visual always stays in sync with the thresholds.
- Supporting views (department dumbbell, tenure box-plot, education stacked bar) sit on the same dashboard for context.

## Live version

[Open on Tableau Public](https://public.tableau.com/app/profile/anderson.rumuy/viz/Operators_17767371215810/Dashboard)
