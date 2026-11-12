# Winter HAB Analysis: Chesapeake Bay Dinoflagellate Data

This project explores two winter–spring bloom-forming dinoflagellates in the Chesapeake Bay, *Heterocapsa triquetra* and *Prorocentrum minimum*. It combines more than 40 years (1984–2025) of Chesapeake Bay Program (CBP) cell counts, surface water temperature, and salinity from 6 monitoring locations in the Upper, Middle, and Lower Bay (CB1.1, CB2.2, CB4.3C, CB5.2, WE4.2, and LE5.5/LE5.5-W) to describe when and where each species occurs and blooms, and the temperature and salinity conditions associated with high abundances. This work also supports my Master's thesis research on these species' distribution and environmental drivers.

## Central question

How do temperature and salinity shape when and where *H. triquetra* and *P. minimum* reach high abundances in the Chesapeake Bay?

1. When and where do the two species occur and bloom?
2. What temperature and salinity conditions are associated with high abundances?
3. Can temperature, salinity, and season predict whether each species is present or at high abundance?

## Data

All phytoplankton and water quality data are public and come from the Chesapeake Bay Program DataHub. The raw downloads were combined into one spreadsheet per dataset, which are included in the `Data` folder.

- **Phytoplankton counts** (cells/L): CBP Phytoplankton Monitoring, taxonomic counts. https://datahub.chesapeakebay.net/LivingResources (Plankton → Phytoplankton → Taxonomic Data). Also described at https://www.chesapeakebay.net/what/downloads/baywide-cbp-plankton-database
- **Temperature (°C) and salinity (ppt)**: CBP Tidal Water Quality Monitoring (MAIN project, parameters WTEMP and SALINITY). https://datahub.chesapeakebay.net/WaterQuality

Files in `Data`:
- `CompiledPhytoplanktonData.xlsx`: compiled phytoplankton counts, 1984–2025
- `CompiledTSData.xlsx`: compiled temperature and salinity profiles, 1984–2026
- `hab_surface_compiled.csv`: the cleaned surface dataset (one row per station per sampling date, with both datasets matched), created by the notebook
- `chesapeake_land.geojson`: land outline for the station map, from Natural Earth 10 m land polygons (public domain, https://www.naturalearthdata.com), clipped to the Chesapeake Bay area

## Repository structure

```
Class-Project/
├── README.md
├── Data/
│   ├── CompiledPhytoplanktonData.xlsx
│   ├── CompiledTSData.xlsx
│   ├── hab_surface_compiled.csv
│   └── chesapeake_land.geojson
└── Code/
    ├── winter_hab_analysis.ipynb
    └── AI_Citation.txt
```

## How to run

1. Download or clone this repository, keeping the folder structure the same (the notebook finds the data with the path `../Data/`).
2. Install the required Python packages (for example, in an Anaconda environment):
   ```
   conda install pandas numpy matplotlib openpyxl scikit-learn
   ```
3. Open Jupyter from the repository folder, open `Code/winter_hab_analysis.ipynb`, and run Kernel → Restart & Run All. Loading the two spreadsheets takes a minute or two.

The notebook runs from top to bottom in this order:
- **Data:** sources and access, compiling the two CBP datasets into one surface dataset (saved as `Data/hab_surface_compiled.csv`), spatial and temporal coverage, data overlap, and surface temperature and salinity conditions.
- **Part 1:** bloom definitions and patterns over time, space, and season.
- **Part 2:** temperature and salinity conditions associated with high abundances.
- **Part 3:** k-means clustering of temperature–salinity regimes.
- **Part 4:** KNN classification of presence and high abundance.
- **Summary:** main findings, limitations, and references.

## Main findings

*H. triquetra* is a cold-water (below ~10–12 °C), moderately salty winter–spring species of the Middle and Lower Bay. *P. minimum* occurs year-round in brackish to salty water and reaches high abundances mainly in spring, with blooms concentrated in the Middle Bay in April and May. Temperature, salinity, and season predict where and when each species occurs well, but not when it reaches high abundance.

## AI use

I used Claude (Anthropic) to help compile the raw CBP data downloads, write and debug notebook code, and draft explanatory text. Details are in `Code/AI_Citation.txt`.

## Author

Katie McCormick, Master's student, Advanced Environmental Data Science (OEAS 805), Fall 2026