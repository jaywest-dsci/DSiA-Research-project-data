# Data Science in Action — MCLS vs. CAHOOTS Handoff Analysis

Comparing how often MCLS and CAHOOTS calls get handed off to law enforcement,
and how MCLS outcomes shifted after CAHOOTS stopped serving Eugene in April 2025.

## Research Questions

- **RQ1:** How often do MCLS or CAHOOTS calls result in a handoff to law enforcement?
- **RQ2:** How do MCLS outcomes vary between when CAHOOTS was operational and after they stopped?

## Project Structure
```
Data Science in Action/
├── main.ipynb
├── MCSLC.xlsx
└── EPD_data/
    ├── EugeneCAD2015noloc.csv
    ├── EugeneCAD2016noloc.csv
    ├── …
    └── EugeneCAD2025noloc.csv
```
## Dependencies

Python 3.13, `pandas`, `numpy`


## How to Run

Open `main.ipynb` and run cells top to bottom. Sections:

1. Imports
2. Data Load
3. Cahoot Clean
4. MCLS Clean
5. Build EPD_handoff — CAHOOTS
6. Build EPD_handoff — MCLS

## The `epd_handoff` Variable

Binary outcome: `1` = call resulted in law enforcement involvement, `0` = it didn't.
Coded differently for each dataset.

- **CAHOOTS:** `1` when `closed_as` is `REFERRED TO OTHER AGENCY`, `RELAYED TO LANE COUNTY SHERIFFS OFFICE`, `RELAYED TO OREGON STATE POLICE`, or `UNIFORM TRAFFIC CITATION ISSUED`. → 753 of 55,134 calls.
- **MCLS:** `1` when `Disposition == "Arrest"`. MCLS has no arrest authority, so an arrest implies EPD involvement. → 16 of 4,682 dispatches.
