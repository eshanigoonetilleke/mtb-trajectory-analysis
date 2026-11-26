# Mtb RNAP conformational dynamics: TS-DAR and tICA-MSM analysis

All data and the trained TS-DAR model are archived on Zenodo: https://doi.org/10.5281/zenodo.24548428

Contents:
1. TS-DAR.ipynb: loads the spectral oASIS features, assigns frames to states with the trained TS-DAR model, computes OOD scores, state centers and transition-state frames, and builds and validates the MSM on the TS-DAR states. Uses: spectral_oasis/, ts-dar_4-state_model/
 
2. MSM.ipynb: k-means clustering, PCCA+ lumping, ITS and CK tests. Uses: tica_trajs_2000_100.npy, label_2000.txt
 
3. environment.yml: Conda environment used to run both notebooks.

Setup:
1. Create the environment:
 
       conda env create -f environment.yml
 
2. Download these files from Zenodo (https://doi.org/10.5281/zenodo.24548428) into this
   directory:
 
       spectral_oasis.tar.gz
       ts-dar_4-state_model.tar.gz
       tica_trajs_2000_100.npy
       label_2000.txt
 
3. Extract the two archives:
 
       tar -xzf spectral_oasis.tar.gz
       tar -xzf ts-dar_4-state_model.tar.gz
 
All paths in the notebooks are relative, so the directory must look like:
 
    TS-DAR.ipynb
    MSM.ipynb
    environment.yml
    label_2000.txt
    tica_trajs_2000_100.npy
    ts-dar_4-state_model/
    spectral_oasis/

Notes:
1. Trajectory indices printed in both notebooks follow one order: RUN 0-251, then CLONE 0-4 within each RUN, skipping the 26 missing RUN/CLONE pairs listed in the Zenodo README.
 
2. TS-DAR state labels: TS-DAR.ipynb uses label_map to convert TS-DAR output indices to the state numbers used in the figures and paper:
 
    0 -> State 3
    1 -> State 4
    2 -> State 2
    3 -> State 1
 
Requirements:
Python 3.9, numpy, pandas, matplotlib, joblib, PyTorch, MSMBuilder, and TS-DAR (package name: tsdar, https://github.com/xuhuihuang/ts-dar). Exact versions are in environment.yml.

TS-DAR method citation:
Liu, B., Boysen, J.G., Unarta, I.C. et al. Exploring transition states of protein conformational changes via out-of-distribution detection in the hyperspherical latent space. Nat. Commun. 16, 349 (2025). https://doi.org/10.1038/s41467-024-55228-4
