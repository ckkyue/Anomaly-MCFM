# Anomaly-MCFM
This repository contains the code (Z Real Data.ipynb) that compares MCFM theoretical calculations with CMS pseudodata and detects anomalies using the One-Class SVM machine learning method. The generated figures are stored in the folder "Figure MCFM Real Data". Additionally, the folder "Result MCFM Real Data" contains the CMS pseudodata and MCFM results.

# Running MCFM-10.3
To install MCFM-10.3, please refer to the instructions provided at https://mcfm.fnal.gov/. The input configurations of the MCFM calculations can be controlled by modifying the file Bin/input_z.ini, and adjustments to the binning of the produced histograms can be made using nplotter_Z_new.f90.

# Folder "Result MCFM Real Data"
The CMS pseudodata is stored in the file fitresult_prefit.hdf5, which needs to be opened using h5py. The other .txt files are the MCFM results.

# Libraries
Ensure that you have installed the following libraries before running Z Real Data.ipynb:
```bash
pip install h5py
pip install matplotlib
pip install numpy
pip install seaborn
pip install scikit-learn
pip install tqdm
```
