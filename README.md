# Winter HAB Analysis: Chesapeake Bay Dinoflagellate Data

This project explores two winter–spring bloom-forming dinoflagellates in the Chesapeake Bay, *Heterocapsa triquetra* and *Prorocentrum minimum*. It combines more than 40 years (1984–2025) of Chesapeake Bay Program (CBP) cell counts, surface water temperature, and salinity from 6 monitoring locations in the Upper, Middle, and Lower Bay (CB1.1, CB2.2, CB4.3C, CB5.2, WE4.2, and LE5.5/LE5.5-W) to describe when and where each species occurs and blooms, and the temperature and salinity conditions associated with high abundances. This work also supports my Master's thesis research on these species' distribution and environmental drivers.

## Central question

How do temperature and salinity shape when and where *H. triquetra* and *P. minimum* reach high abundances in the Chesapeake Bay?

1. When and where do the two species occur and bloom?
2. What temperature and salinity conditions are associated with high abundances?
3. Can temperature, salinity, and season predict whether each species is present or at high abundance?

## Data

All data are public and come from the Chesapeake Bay Program DataHub. The raw downloads were combined into one spreadsheet per dataset, which are included in the `Data` folder.

- **Phytoplankton counts** (cells/L): CBP Phytoplankton Monitoring, taxonomic counts. https://datahub.chesapeakebay.net/LivingResources (Plankton → Phytoplankton → Taxonomic Data). Also described at https://www.chesapeakebay.net/what/downloads/baywide-cbp-plankton-database
- **Temperature (°C) and salinity (ppt)**: CBP Tidal Water Quality Monitoring (MAIN project, parameters WTEMP and SALINITY). https://datahub.chesapeakebay.net/WaterQuality

Files in `Data`:
- `CompiledPhytoplanktonData.xlsx`: compiled phytoplankton counts, 1984–2025
- `CompiledTSData.xlsx`: compiled temperature and salinity profiles, 1984–2026
- `hab_surface_compiled.csv`: the cleaned surface dataset (one row per station per sampling date, both datasets matched), created by the EDA notebook and used by the analysis notebook

## Repository structure

Class-Project/
├── README.md
├── Data/
│ ├── CompiledPhytoplanktonData.xlsx
│ ├── CompiledTSData.xlsx
│ └── hab_surface_compiled.csv
└── Code/
├── hab_dinoflagellate_exploratory_data_analysis.ipynb
├── HAB_Bloom_descriptive_analysis.ipynb
└── AI_Citation.txt


## How to run

1. Download or clone this repository, keeping the folder structure the same (the notebooks find the data with the path `../Data/`).
2. Install the required Python packages (for example, in an Anaconda environment):

conda install pandas numpy matplotlib openpyxl scikit-learn

3. Open Jupyter from the repository folder and run the notebooks in this order (Kernel → Restart & Run All):
   1. `Code/hab_dinoflagellate_exploratory_data_analysis.ipynb`: exploratory data analysis. Combines the two spreadsheets, restricts the data to the surface layer, keeps only dates with both datasets, and saves `Data/hab_surface_compiled.csv`. Also describes data sources, spatial and temporal coverage, and overlap. Loading the spreadsheets takes a minute or two.
   2. `Code/HAB_Bloom_descriptive_analysis.ipynb`: main analysis. Bloom definitions and patterns over time, space, and season (Part 1); temperature and salinity conditions (Part 2); k-means clustering of temperature–salinity regimes (Part 3); and KNN classification of presence and high abundance (Part 4).

`hab_surface_compiled.csv` is already included, so the analysis notebook can also be run on its own.

## Main findings

*H. triquetra* is a cold-water (below ~10–12 °C), moderately salty winter–spring species of the Middle and Lower Bay. *P. minimum* occurs year-round in brackish to salty water and reaches high abundances mainly in spring, with blooms concentrated in the Middle Bay in April and May. Temperature, salinity, and season predict where and when each species occurs well, but not when it reaches high abundance.

## AI use

I used Claude (Anthropic) to help compile the raw CBP data downloads, write and debug notebook code, and draft explanatory text. Details are in `Code/AI_Citation.txt`.

## Author

Katie McCormick, Master's student, Advanced Environmental Data Science (OEAS 805), Fall 2026
