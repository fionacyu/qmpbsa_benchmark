# fep_benchmark

## Single Point Energy Calculations
- `xyz_files`: contains all the .xyz files for each of the targets used for MBE/MP2/cc-pVDZ single point energy calculations. 
- All .xyz files are named in the same style, specifically, `target.ligand.cluster_framenumber.xyz` (e.g. `tyk2.lig_ejm_55.cluster_884.xyz`, `target = tyk2`, `ligand = lig_ejm_55`, `framenumber = 884`).

## Poisson Boltzmann Surface Area Calculations
- `pbsa_files`: contains all the concatenated input .json files for pbsa calculations. Each concatenanted input .json file contains 1001 structures (corresponding to each of the frames sampled from the MD simulation) and contains the geometry and atomic partial charges.

- `pbsa_files` contains many compressed .zip files, when all files are expanded, `pbsa_files` takes on the following form:
```
├── bace
│   ├── lig_13a 
│   │   ├── complex.qdx.json
│   │   ├── ligand.qdx.json
│   │   ├── protein.qdx.json
│   ├── ...
├── cdk2
├── jnk1
├── mcl1
├── p38
├── ptp1b
├── thrombin
├── tyk2
```
