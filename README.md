# Study data

This directory contains study datasets for a study with 36 participants and five coded experimental conditions. Raw per-participant survey exports are not included.

Last verified: 2026-07-21.

## Contents

```text
data/
├── Demo_TOT.xlsx
├── Final_TOT.xlsx
├── Survey_Condition_TOT.xlsx
├── Zeiten.xlsx
├── Short_UEQ_Data_Analysis_Tool.xlsx
└── items.json
```

The five Excel workbooks and one JSON file occupy approximately 460 KB. The macOS `.DS_Store` file, if present locally, is not part of the dataset and should not be committed.

## Files

### `Demo_TOT.xlsx`

A participant-level demographic and Affinity for Technology Interaction (ATI) dataset.

- Sheet: `Survey_Results`
- Shape: 37 rows × 13 columns (one header row and 36 participant rows)
- Variables:
  - `Participant ID`
  - `Age`
  - `Gender`
  - `VR/AR/MR Experience`
  - `ATI1`–`ATI9`
- Formulas: none

The `Age` column has one missing participant value.

### `Final_TOT.xlsx`

A participant-level post-study dataset.

- Sheet: `Survey_Results`
- Shape: 37 rows × 3 columns (one header row and 36 participant rows)
- Variables:
  - `Participant ID`
  - `Condition Preference`
  - `Open comment`
- Formulas: none

`Condition Preference` contains multiple labeling schemes, including spatial labels and coded configurations. Normalize these categories before analysis if they are intended to represent the same underlying comparison.

### `Survey_Condition_TOT.xlsx`

The main repeated-measures condition dataset.

- Sheet: `Survey_Results`
- Shape: 55 rows × 182 columns
- Coverage: 36 participants × 5 conditions
- Formulas: none

The workbook uses a wide, transposed layout:

- row 1 identifies the participant, repeated across five columns;
- row 2 identifies conditions `1`–`5`;
- column A contains measure or questionnaire-item names;
- column B contains the label `Questions`/`na` rather than observations;
- columns C–FZ contain the participant-condition observations.

The measured variables are:

- performance/activity measures:
  - `Solution checked`
  - `Balls grabbed`
  - `Parts painted`
  - `Faults`
  - `Time`
- six NASA-TLX items:
  - mental demand
  - physical demand
  - temporal demand
  - performance
  - effort
  - frustration
- eight Short User Experience Questionnaire (`UEQ-S`) items;
- 34 Networked Minds items covering:
  - first-order co-presence;
  - perceived attentional engagement;
  - perceived emotional contagion;
  - perceived comprehension;
  - perceived behavioral interdependence.

For most statistical workflows, reshape this workbook to a long table with one row per participant-condition observation and columns for `Participant ID`, `Condition`, and each measure.

### `Zeiten.xlsx`

A supporting time table (`Zeiten` is German for “times”).

- Sheet: `Tabelle1`
- Populated structure: one header row, five condition rows, and columns `1B`–`7B`
- Formulas: none

Time values are stored as Excel serial day fractions. Preserve the workbook's time formatting or convert them explicitly to the required unit before analysis.

### `Short_UEQ_Data_Analysis_Tool.xlsx`

A formula-driven Short UEQ analysis workbook attributed inside the file to Dr. Martin Schrepp. Its input sheet currently contains 13 response rows, so it should not be assumed to represent all 36 participants in the consolidated datasets.

The workbook contains ten sheets:

| Sheet | Purpose |
| --- | --- |
| `Read_First` | Instructions and language selection |
| `Data` | Eight-item UEQ-S input data |
| `DT` | Responses transformed to the −3 to +3 scale and participant-level scale scores |
| `Results` | Item and scale summaries |
| `Confidence_Intervals` | Confidence intervals for items and scales |
| `Scale_Consistency` | Item correlations and Cronbach's alpha calculations |
| `Benchmark` | Comparison with the tool's benchmark data |
| `Inconsistencies` | Detection of potentially inconsistent response patterns |
| `Items` | Multilingual item wording |
| `Sample_Size` | Sample-size and precision guidance |

### `items.json`

Multilingual labels corresponding to the UEQ-S workbook's `Items` sheet.

- 36 languages
- 18 fields per language
- 16 fields for the left/right wording of eight UEQ-S items
- two scale labels: Pragmatic Quality and Hedonic Quality
