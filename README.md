# Combining BGC-Argo floats and satellite observations for water column estimations of the particulate backscattering coefficient

Estimating bbp profiles in the upper ocean using BGC-Argo floats and satellite observations.

The study examines how satellite-derived sea surface optical properties, combined with BGC-Argo profiles, can be used to reconstruct the vertical structure of bbp throughout the upper 250 meters of the water column. It builds on the SOCA2016 method developed by Sauzède et al. (2016).

Sauzède et al., 2016 — https://doi.org/10.1002/2015JC011408

## Related Publication

The study is described in detail in:

> **Combining BGC-Argo floats and satellite observations for water column estimations of the particulate backscattering coefficient**  
> Jorge García-Jiménez, Ana B. Ruescas, Julia Amorós-López, Raphaëlle Sauzède  
> *EGUsphere (2025)*  
> [🔗 Read the article](TODO)

## Regions of Interest

- North Atlantic
- Subtropical Gyres

<div align="center">
  <img src="docs/img/Map.png" alt="Map" width="90%"/>
</div>

## Modeling Approach

- **Model type**: Multi-output Random Forest Regressor
- **Input features**:
  - Satellite: OLCI reflectances (12 wavelengths), C2RCC IOPs (*apig, adet, agelb, bpart, bwit, atot, btot*)
  - GlocColour: reflectances at 5 wavelengths
  - GlobalOcean: Sea Level Anomaly (SLA)
  - BGC-Argo Float profiles: temperature, salinity, density, spiciness (via PCA)
  - Mixed Layer Depth (MLD)
  - Spatial-temporal: latitude, longitude, day of year
- **Target**: Particulate Backscattering Coefficient (Bbp):
  - 26 depths for the 0–50 m model  
  - 126 depths for the 0–250 m model
  
## Model Performance – Deep Profiles (0–250 m)

<div align="center">
  <img src="docs/img/250.jpg" alt="Model Performance 250m" width="90%"/>
</div>

## How to Cite

If you use this repository, please cite our paper:

### APA

> García-Jiménez, J., Ruescas, A. B., Amorós-López, J., & Sauzède, R. (2025). *Combining BGC-Argo floats and satellite observations for water column estimations of the particulate backscattering coefficient*. EGUsphere. https://doi.org/10.5194/egusphere-2024-3942

### BibTeX

```bibtex
@article{garcia-jimenez2025bbp,
  author    = {García-Jiménez, Jorge and Ruescas, Ana B. and Amorós-López, Julia and Sauzède, Raphaëlle},
  title     = {Combining BGC-Argo floats and satellite observations for water column estimations of the particulate backscattering coefficient},
  journal   = {EGUsphere},
  year      = {2025},
  doi       = {10.5194/egusphere-2024-3942}
}
```

## Repository Structure

<pre>
SatArgoBbp/
├── src/              
│   ├── models/        # Model training and evaluation scripts
│   ├── features/      # Feature preprocessing (PCA, scaling, transformations)
│   └── utils/         # Plotting, export functions, I/O helpers
├── datasets/          # Processed input datasets (excluded from Git)
├── notebooks/         # Experimentation and experiment comparison notebooks
├── results/           # Outputs: plots, metrics, figures
├── docs/
│   └── img/           # Visuals for README and manuscript (TO DO)
├── .gitignore         
├── README.md
└── pixi.toml          # Project environment and dependencies (managed with Pixi)
</pre>

### How to clone the repository

This project uses [Pixi](https://prefix.dev) for fully reproducible environment management.

### Step 1 — Install Pixi (if not already installed)

```bash
curl -sSf https://pixi.sh/install.sh | bash
```
After installation, restart your terminal or reload your shell:

```bash
exec $SHELL
```

### Step 2 — Clone the Repository

```bash
git clone git@github.com:XXXXXXXXX IPL
cd SatArgoBbp
```
### Step 3 — Set Up the Environment

```bash
pixi install
```
This command reads `pixi.toml` and creates the environment with all dependencies.

---

### Step 4 — Activate the Environment

```bash
pixi shell
```

### Step 5 — Run Notebooks or Scripts

To launch the Jupyter interface:

```bash
jupyter notebook
```

To run a model training TODO:

```bash
python src/models/train_rf.py
```
