# fep_benchmark

# Layout
The single point energy (spe) and poisson boltzmann surface area (pbsa) input and output files are arranged in the following layout:
```
├── spe
│   ├── inputs
│   │   ├── ...
│   ├── outputs
│   │   ├── ...
├── pbsa
│   ├── inputs
│   │   ├── ...
│   ├── outputs
│   │   ├── ...
```

# Inputs
## Single Point Energy Calculations
- `spe/inputs/xyz`: contains all the .xyz files for each of the targets used for MBE/MP2/cc-pVDZ single point energy calculations. 

- All .xyz files are named in the same style, specifically, `target.ligand.cluster_framenumber.xyz` (e.g. `tyk2.lig_ejm_55.cluster_884.xyz`, `target = tyk2`, `ligand = lig_ejm_55`, `framenumber = 884`).

- `spe/inputs/topo`: contains the input .json files used for EXESS and the associated topology. Entries in `"connectivity"` correspond to the bonds broken for fragmentation. 

## Poisson Boltzmann Surface Area Calculations
- `pbsa/inputs`: contains all the concatenated input .json files for pbsa calculations. Each concatenanted input .json file contains 1001 structures (corresponding to each of the frames sampled from the MD simulation) and contains the geometry and atomic partial charges.

- `pbsa/inputs` contains many compressed .zip files, when all files are expanded, the directories are arranged in the following form:
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

- Each of the `complex.qdx.json`, `ligand.qdx.json`, and `protein.qdx.json` contain the concatenated input files. 

- The .json files contain the fields `"geometry"`, `"symbols"` and `"partial_charges"` which are required as input for pbsa calculations.

# Output Energies / Results
