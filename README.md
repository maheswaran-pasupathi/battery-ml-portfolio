# Battery ML Portfolio

A CFD engineer's transition into applied ML — case studies in battery aging, degradation, and thermal-electrochemical coupling, built entirely on open data.

## About this repo

I'm a CFD engineer with 6–10 years of experience in **in-cylinder combustion, engine thermal management, and battery thermal simulation** (Star-CCM+, Ansys Fluent, GT-SUITE). This repo is where I'm applying that physics background to data-driven battery health modeling — partly to build a public, verifiable ML skillset, and partly because the underlying physics (heat generation, thermally-activated degradation kinetics, the aging–heat feedback loop) is the same territory I already work in from the simulation side. The goal is to bring a domain expert's intuition to problems usually approached as pure time-series ML.

This is a portfolio repo, not a production pipeline — each notebook is written to be read and followed, not just run.

## Notebook series

The plan is a three-part arc, each building on the last:

| # | Notebook | Status | Description |
|---|----------|--------|-------------|
| 1 | [`01-nasa-battery-aging-eda.ipynb`](notebooks/01-nasa-battery-aging-eda.ipynb) | **Published** — [view on Kaggle](https://www.kaggle.com/code/maheswaranpasupathi/li-ion-battery-aging-eda-with-a-thermal-engineer) | Exploratory analysis of capacity fade, discharge voltage curves, and temperature rise across cell life. Frames the aging signature through a thermal-engineer's lens (SEI growth, $I^2R$ and entropic heat, the aging–heat feedback loop). |
| 2 | `02-feature-engineering-soh-rul.ipynb` | Planned | Engineer per-cycle features (discharge time, voltage slope, ΔT, knee-point indicators) and train a baseline model for State of Health (SOH) / Remaining Useful Life (RUL) prediction. |
| 3 | `03-sequence-models.ipynb` | Planned | Move from tabular baselines to sequence models (LSTM / transformer-style) on the raw time-series, comparing against the Notebook 2 baseline. |

Each notebook is committed here first, then published to Kaggle once verified end-to-end.

## Data & tools

- **Dataset:** NASA PCoE Li-ion Battery Aging Dataset (public domain, widely used in battery prognostics research).
- **Current input source:** Notebook 1 runs against [`patrickfleith/nasa-battery-life-prediction-dataset-cleaning`](https://www.kaggle.com/code/patrickfleith/nasa-battery-life-prediction-dataset-cleaning) — a cleaned **Kaggle Notebook-Output**, not the raw `nasa-battery-dataset` Dataset directly. If you fork this and re-attach a different input, note that Notebook-Output and Dataset inputs mount at different path patterns on Kaggle (`/kaggle/input/notebooks/<user>/<slug>/` vs `/kaggle/input/<slug>/`) — re-verify paths with `os.walk('/kaggle/input')` before assuming anything carries over.
- **Stack:** Python, pandas, NumPy, matplotlib, seaborn, Jupyter.
- **Planned addition:** [PyBaMM](https://www.pybamm.org/) for generating self-owned, parametric simulation datasets (varying cell properties via the `ParameterValues` API) — this lets future notebooks go beyond what's available in static public datasets, while staying fully open-source and publishable.

## A note on data provenance

No proprietary or employer simulation data is used anywhere in this repo. Everything here is built on open datasets and open-source tools (NASA PCoE, PyBaMM) specifically so the work is transparent, reproducible, and safely shareable.

## Repo structure

```
battery-ml-portfolio/
├── notebooks/
│   ├── 01-nasa-battery-aging-eda.ipynb
│   ├── 02-feature-engineering-soh-rul.ipynb   (planned)
│   └── 03-sequence-models.ipynb               (planned)
└── README.md
```

## Connect

- Kaggle: [maheswaranpasupathi](https://www.kaggle.com/maheswaranpasupathi)
- Feedback, comments, and "you missed X degradation mechanism" critiques are welcome — open an issue or comment directly on the Kaggle notebook.

## License

MIT — see [LICENSE](LICENSE)
