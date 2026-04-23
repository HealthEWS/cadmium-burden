# cadmium-burden
Global Burden of Blood Cadmium Exposure: A Bayesian Hierarchical Modelling Study


Repository Structure
```
├── R/
│   ├── 00_utils.R                 Shared helper functions
│   ├── 01_data_cleaning.R         Outlier detection and smoothing
│   ├── 02_weighted_pooling.R      Within-country weighted aggregation
│   ├── 03_bayesian_gm_model.R     Bayesian hierarchical model for log(GM)
│   ├── 04_bayesian_gsd_model.R    Bayesian hierarchical model for log(GSD)
│   ├── 05_prediction.R            Posterior predictions for 204 countries
│   ├── 06_dose_response.R         Restricted cubic spline dose–response
│   ├── 07_paf_monte_carlo.R       Monte Carlo PAF estimation
│   ├── 08_mrbrt_evidence.R        MR-BRT burden-of-proof analysis
│   └── run_all.R                  Master pipeline script
├── config/
│   └── parameters.R               Centralised analytic parameters
├── data/
│   └── README.md                  Data availability statement
├── output/                        Generated results (not tracked)
├── figures/                       Generated figures (not tracked)
├── CITATION.cff                   Citation metadata
├── DESCRIPTION                    Package metadata and dependencies
├── LICENSE                        GPL-3.0 licence
├── Makefile                       Reproducibility targets
└── .gitignore
```
Requirements
R ≥ 4.3.0
Python ≥ 3.11 with `mrtool` (for MR-BRT analysis only)
Stan toolchain (for `brms`)
R Package Dependencies
Package	Purpose
`brms`	Bayesian regression via Stan
`tidyverse`	Data manipulation and visualisation
`readxl` / `writexl`	Excel I/O
`splines`	Restricted cubic spline basis
`furrr` / `future`	Parallel computation
`bayesplot`	MCMC diagnostics
`MASS`	Multivariate normal sampling
`patchwork`	Figure composition
`reticulate`	Python interoperability
Install all dependencies:
```r
source("config/parameters.R")
install.packages(c(
  "brms", "tidyverse", "readxl", "writexl", "splines",
  "furrr", "future", "bayesplot", "MASS", "patchwork",
  "reticulate", "pracma", "ggthemes", "scales"
))
```
Reproduction
Full pipeline
```bash
make all
```
Step-by-step
```r
source("R/run_all.R")
```
Or execute individual stages:
```r
source("config/parameters.R")
source("R/00_utils.R")
source("R/01_data_cleaning.R")
source("R/02_weighted_pooling.R")
# ... etc.
```
MR-BRT analysis
The burden-of-proof analysis (`08_mrbrt_evidence.R`) requires the `mrtool` Python package. Set up a virtual environment:
```bash
python3 -m venv r-mrtool311
source r-mrtool311/bin/activate
pip install mrtool
```
License
This project is licensed under the GNU General Public License v3.0. See LICENSE for details.
Contact
For questions about the code or data, please open an issue or contact the corresponding author.
