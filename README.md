# Anomaly-MCFM
This repository compares MCFM predictions for the Z-boson observables against CMS pseudodata and then applies a One-Class SVM to flag anomalous bins. The main workflow lives in [Z Real Data.ipynb](Z%20Real%20Data.ipynb), the generated plots are written to [Figure MCFM Real Data](Figure%20MCFM%20Real%20Data), and the input/output data used by the notebook is stored in [Result MCFM Real Data](Result%20MCFM%20Real%20Data).

## Repository Layout
- [Z Real Data.ipynb](Z%20Real%20Data.ipynb): notebook that loads the CMS pseudodata, reads the MCFM text outputs, compares theory to data, and runs anomaly detection.
- [MCFM-10.3](MCFM-10.3): local MCFM source tree and the Z-process input configuration.
- [Result MCFM Real Data](Result%20MCFM%20Real%20Data): CMS pseudodata, binned MCFM outputs, and intermediate text results used by the notebook.
- [Figure MCFM Real Data](Figure%20MCFM%20Real%20Data): saved comparison plots and novelty-detection figures.

## Workflow
1. Build and run MCFM from [MCFM-10.3/Bin](MCFM-10.3/Bin) using the Z-process input file.
2. Open [Z Real Data.ipynb](Z%20Real%20Data.ipynb) to load the HDF5 pseudodata and the generated MCFM text files.
3. Compare the CMS reference distribution to MCFM predictions for `pT` and `|Y|`.
4. Run the One-Class SVM scans to identify bins that behave differently from the training distribution.
5. Review the saved figures in [Figure MCFM Real Data](Figure%20MCFM%20Real%20Data).

## Running MCFM
The MCFM inputs for this study are defined in [MCFM-10.3/Bin/input_Z.ini](MCFM-10.3/Bin/input_Z.ini). The custom histogram binning used by the notebook is implemented in [MCFM-10.3/src/User/nplotter_Z_new.f90](MCFM-10.3/src/User/nplotter_Z_new.f90).

From the MCFM binary directory, build and run the Z configuration with:

```bash
cd MCFM-10.3/Bin
make -j256
export OMP_STACKSIZE=512000
./mcfm input_Z.ini
```

If you use a different input file, replace `input_Z.ini` with the appropriate configuration file.

## Data Files
- `fitresult_prefit.hdf5` is the CMS pseudodata file read by the notebook through `h5py`.
- The `Z_data_*.txt` files are the MCFM outputs used for the comparisons.
- The filenames encode the PDF set (`NNPDF31` or `MSHT20`), perturbative order (`resNLOp` or `resNNLO`), and the observable (`pT` or `eta`).
- The `pT_3` to `pT_12` files are the binned slices used in the bin-by-bin comparison and anomaly detection steps.

## Python Dependencies
The notebook imports the following Python packages:

```bash
pip install h5py matplotlib numpy seaborn scikit-learn tqdm
```

## Outputs
- The comparison plots `sigma vs pT`, `sigma vs abs(Y)`, and `sigma vs bin` are written to [Figure MCFM Real Data](Figure%20MCFM%20Real%20Data).
- The novelty-detection plots are saved in the same folder, one image per parameter choice and PDF/order combination.

## Notes
- The notebook assumes the repository root as the working directory.
- The custom MCFM plotter uses the `pt34_fine` and `y34` histograms, plus the `pT` slice histograms used for the anomaly scan.
