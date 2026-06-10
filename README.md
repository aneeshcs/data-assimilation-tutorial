# Data Assimilation Tutorial: 3DVAR, 4DVAR, and EnKF on Lorenz 63

Interactive tutorial for the **FERS Summer School on AI and Machine Learning for Earth System Modeling and Prediction**.

## What you will learn

- The **twin-experiment** framework for testing data assimilation algorithms
- **3DVAR** — variational assimilation at a single time (Tikhonov least squares)
- **4DVAR** — variational assimilation over a time window (BPTT for physics models)
- **Ensemble Kalman Filter (EnKF)** — sequential, flow-dependent Bayesian filtering
- How ensemble spread relates to forecast error (reliability)
- How observation frequency affects analysis quality

The **Lorenz 63** chaotic system is used as the testbed throughout — it is simple enough to run in seconds but rich enough to expose all the core DA challenges: sensitive dependence on initial conditions, non-Gaussian error growth, and flow-dependent uncertainty.

## Running the tutorial

### Option A — Marimo (interactive, reactive)

```bash
pip install marimo numpy scipy matplotlib
marimo run tutorial.py        # view-only, interactive
marimo edit tutorial.py       # editable notebook
```

Open the URL printed to the terminal. Sliders for ensemble size and inflation factor update results in real time.

### Option B — JupyterHub / Jupyter Notebook

Export the marimo notebook to a Jupyter notebook:

```bash
marimo export ipynb tutorial.py -o tutorial.ipynb
```

Then upload `tutorial.ipynb` to your JupyterHub instance and open it.

### Option C — Google Colab / Binder

Upload `tutorial.ipynb` to Colab or add a `binder/` configuration to this repo.

## Repository layout

```
data-assimilation-tutorial/
├── tutorial.py        # Marimo notebook (source of truth)
├── tutorial.ipynb     # Jupyter export (generated)
├── requirements.txt   # Python dependencies
└── README.md
```

## Dependencies

| Package | Purpose |
|---------|---------|
| `numpy` | Numerics |
| `scipy` | ODE integration, optimisation |
| `matplotlib` | Plotting |
| `marimo` | Interactive notebook runtime |

## Background

### The algorithms in one sentence each

- **3DVAR**: minimise a regularised misfit between a background state and observations at a single time.
- **4DVAR**: same, but the state is an initial condition whose model trajectory must fit observations distributed over a time window — gradient via adjoint or finite differences.
- **EnKF**: propagate an ensemble of model states; use the sample covariance as a flow-dependent background error covariance; update each member with perturbed observations.

### Connection to machine learning

| DA concept | ML analogue |
|-----------|-------------|
| 3DVAR cost function | Ridge regression |
| 4DVAR adjoint | Backpropagation through time (BPTT) |
| EnKF | Monte-Carlo / particle Bayes filter |
| Ensemble spread | Epistemic uncertainty in BNNs |

## Licence

MIT — free to use, adapt, and teach with.
