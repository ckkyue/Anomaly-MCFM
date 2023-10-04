# Anomaly-MCFM
This repository contains the code (Z Real Data.ipynb) that compares MCFM theoretical calculations with CMS pseudodata and detects anomalies using the One-Class SVM machine learning method. The generated figures are stored in the "Figure MCFM Real Data" folder. Additionally, the "Result MCFM Real Data" folder contains the CMS pseudodata and MCFM results.

# MCFM-10.3
To install MCFM-10.3, please refer to the instructions provided at https://mcfm.fnal.gov/. The input configurations of the MCFM calculations can be controlled by modifying the Bin/input_z.ini file, and adjustments to the binning of the produced histograms can be made using nplotter_Z_new.f90.

The MCFM-10.3 folder contains codes that define input configurations and binning of histograms produced in MCFM. To start the program, first go to Bin
```bash
cd MCFM-10.3/Bin
```
and run
```bash
make -j256 ; export OMP_STACKSIZE=512000 ; ./mcfm input_Z.ini
```
which you should replace input_Z.ini with the file that provides the input configuration.

# "Result MCFM Real Data" Folder
The CMS pseudodata is stored in the fitresult_prefit.hdf5 file, which needs to be opened using h5py. The other .txt files are the MCFM results.

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
