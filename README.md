# Floating Platform Design and Performance Dataset

English-language data prepared to accompany **[Multi-Objective Optimization for Semi-Submersible Drilling Platform Structures Based on Advanced FAHP-CRITIC Evaluation Method]**.

**Release preparation status:** dataset labels have been translated. Authors must complete the paper metadata, units, variable definitions, and the two headerless dataset descriptions before publication.

## Related publication

- Authors: [Jianbo Li, Chen An, Honglin Che, Zhongheng Lai, Jixiang Zhang, Menglan Duan]
- Paper title: [Multi-Objective Optimization for Semi-Submersible Drilling Platform Structures Based on Advanced FAHP-CRITIC Evaluation Method]
- Contact: [anchen@cup.edu.cn]

## Files

`data/xlsx/` contains the eight translated workbooks. `data/csv/` contains UTF-8 CSV counterparts for inspection and reuse. All workbooks retain the sheet name `Sheet1` and original cell positions. The CSV files retain the blank separator column G in the six labeled datasets and omit only trailing empty columns I–L. The two headerless files remain headerless: their first row is data.

| Workbook | Data rows | Layout |
| --- | ---: | --- |
| `optimization_schemes.xlsx` | 36 | A–F: unlabeled numeric columns |
| `initial_metacentric_height.xlsx` | 318 | A–F: inputs; H: response; G: blank |
| `objective_weights.xlsx` | 36 | A–F: unlabeled numeric columns |
| `platform_weight.xlsx` | 318 | A–F: inputs; H: response; G: blank |
| `maximum_heave_motion.xlsx` | 318 | A–F: inputs; H: response; G: blank |
| `maximum_towing_resistance.xlsx` | 318 | A–F: inputs; H: response; G: blank |
| `maximum_surge_motion.xlsx` | 318 | A–F: inputs; H: response; G: blank |
| `minimum_air_gap.xlsx` | 318 | A–F: inputs; H: response; G: blank |

## Variable definitions

For the six labeled datasets, the source headers identify columns A–F as Float Length, Float Width, Float Height, Float Spacing, Draft, and Transverse Brace Diameter. Column H is the response named by the workbook. `Float` is a conservative translation of the source term; authors should confirm whether `Pontoon` is the term used in the paper. Float Spacing must be defined as centerline spacing, clear spacing, or the actual convention used in the study.

See `docs/data_dictionary.csv` for per-file column labels. No units, scaling factors, coordinate conventions, motion statistics, load cases, or data-generation methods were supplied in the workbooks. Add those details here before release. In particular, define the platform weight scale and whether the quantity is mass or force, the towing-resistance scale, the motion statistic and its units, and the metacentric-height convention.

`optimization_schemes.xlsx` and `objective_weights.xlsx` each contain 36 rows and six unlabeled columns. Their names translate the source filenames only. The contents of the latter have not been verified to be normalized weights. Authors must identify the columns, explain the weighting method, and state whether the file contains weights or the decision matrix used to calculate them.

## Provenance and processing

- Original data supplied by the authors; exact measurement/simulation method: [INSERT METHOD].
- Existing Chinese cell labels and filenames were translated into English.
- No numerical transformations, normalization, imputation, sorting, or deduplication were performed.
- Existing blank cells and row order were retained. English-header columns were widened for readability.
- No missing headers or units were invented. No train/test split was assigned.
- Numerical cell values were compared with the supplied workbooks after export; see `docs/validation_report.json`.
- `docs/file_name_mapping.csv` records original and translated filenames. Its original-name column intentionally contains Chinese for provenance.

## Reuse example

```python
import pandas as pd

df = pd.read_csv("data/csv/initial_metacentric_height.csv")
X = df.iloc[:, :6]   # Six source-labeled design variables
y = df.iloc[:, 7]    # Initial Metacentric Height

# Important: these two files have no header row.
schemes = pd.read_csv("data/csv/optimization_schemes.csv", header=None)
weighting_data = pd.read_csv("data/csv/objective_weights.csv", header=None)
```

To reproduce the paper, supply the model code, preprocessing procedure, train/validation/test indices, random seed, hyperparameters, and software versions. These are not included in the supplied spreadsheets.


## Version history

- Planned v1.0.0: initial English-language dataset release; release date to be supplied by the authors.
