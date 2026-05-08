# Mapping the Sea

A visual analysis of global fishing activity patterns, gear damage, and
unknown-flag vessels using Global Fishing Watch (GFW) AIS data,
2016–2024.

This repository holds the **code, notebooks, and visualization assets**
that back the project report and interactive Tableau dashboard. The
written report is maintained separately.

## Live dashboard

Tableau Public:
<https://public.tableau.com/app/profile/biniyam.zergaw/viz/ShippingVesselsMovement/FishingActivityandEffects>

## Repository layout

```
.
├── python_analysis/
│   ├── fishing_vessel_data_eda.ipynb  # Outlier diagnosis + p99 winsorisation
│   ├── yearly_fishing_trend.ipynb     # 2024 trend / flag / gear analysis
│   └── results/
│       ├── notebook/                  # Static figures rendered by the notebooks
│       └── tableau/                   # Dashboard screenshots used in the report
├── tableau files/                     # Tableau .twb workbooks
└── data/                              # NOT in git — 75 GB of GFW CSVs (see below)
```

## Data — not in git

The `data/` folder is excluded by `.gitignore` because the raw GFW
`fleet-monthly-10-v3` CSV archive is ~75 GB. To reproduce the analysis,
download the dataset directly from Global Fishing Watch:

<https://globalfishingwatch.org/datasets-and-code/>

After download, place the monthly CSVs at:

```
data/fleet_monthly/fleet-monthly-csvs-10-v3-YYYY/
data/fleet_daily/fleet-daily-csvs-100-v3-YYYY/
```

so that the notebook's `DATA_DIR = PROJECT_ROOT / "data" / "fleet_monthly"`
path resolves correctly.

The supplementary gear-effects scoring matrix
(`data/gear_effects_radar.csv`, 16 gear types × 7 impact categories) is
small enough to keep in the repo if desired.

## Reproducing the analysis

1. Clone the repo and set up a Python environment:

   ```bash
   pip install pandas numpy matplotlib seaborn scipy statsmodels
   ```

2. Download the GFW data into `data/` (see above).
3. Open the notebooks under `python_analysis/` in Jupyter and run all
   cells. Figures are written to `python_analysis/results/notebook/`.
4. The Tableau workbook
   `tableau files/Shipping Vessels Movement.twb` connects to the same
   data; the published version is on Tableau Public (link above).

## Author

Biniyam Zergaw — `bz24@fordham.edu`
Data Visualization Project, May 2026.
