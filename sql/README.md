# SQL notes

The original production data lived in a manufacturing HR + DCS logging system and required cleaning (see `docs/issues-log.md`).

For this **portfolio version** an artificial but realistic clean dataset was created (`data/sample/raw_data.csv`). Consequently no production extraction scripts are published.

If you want to reproduce a similar cleaning pipeline on your own data, the typical pattern used was:

```sql
-- Example pattern only (not production code)
WITH cleaned AS (
  SELECT
    operator_id,
    -- standardize department names
    CASE
      WHEN LOWER(department) LIKE '%digester%' THEN 'Fiberline - Digester'
      WHEN LOWER(department) LIKE '%bleach%'   THEN 'Fiberline - Bleaching'
      WHEN LOWER(department) LIKE '%paper%'    THEN 'Paper Machine'
      WHEN LOWER(department) LIKE '%power%'    THEN 'Power Plant'
      WHEN LOWER(department) LIKE '%recovery%' OR LOWER(department) LIKE '%boiler%' THEN 'Recovery Boiler'
      ELSE department
    END AS department,
    education_level,
    tenure_years,
    dlp_score,
    pqs_score
  FROM source_table
  WHERE pqs_score IS NOT NULL          -- exclude downtime periods
)
SELECT *
FROM cleaned QUALIFY ROW_NUMBER() OVER (PARTITION BY operator_id ORDER BY assessment_date DESC) = 1;
```

The published sample is already the output of an equivalent process and can be used directly with the Tableau workbook.
