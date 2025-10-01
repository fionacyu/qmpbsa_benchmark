# fep_benchmark
This repository contains the input files (topologies and structures) and output energies for EXESS SPE and PBSA calculations for 198 protein-ligand systems. 

| Target   | nligands |
|----------|----------|
| BACE     | 36       |
| CDK2     | 16       |
| JNK1     | 21       |
| MCL1     | 42       |
| P38      | 34       |
| PTP1B    | 23       |
| thrombin | 10       |
| TYK2     | 16       |

# Data Layout
- `qmpbsa_results.xlsx`: contains all the gas phase and solvation energies for all targets. All energies listed therein are in kJ/mol

- `spe` contains data related to single point energy calculations with EXESS

- `pbsa` contains data related to poisson boltzmann surface area calculations

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
## Single Point Energy Calculations
Output energy files are arranged in the following layout

```
├── mbe2
│   ├── bace
│   │   ├── lig_13a
│   │   │   ├── bacelig_13acluster_0.json
│   │   │   ├── bacelig_13acluster_114.json
│   │   │   ├── ...
│   │   ├── ...
│   ├── cdk2
│   ├── jnk1
│   ├── mcl1
│   ├── p38
│   ├── ptp1b
│   ├── thrombin
│   ├── tyk2
├── mbe3
│   ├── bace
│   │   ├── lig_13a
│   │   │   ├── bacelig_13acluster_0.json
│   │   │   ├── bacelig_13acluster_114.json
│   │   │   ├── ...
│   │   ├── ...
│   ├── cdk2
│   ├── jnk1
│   ├── mcl1
│   ├── p38
│   ├── ptp1b
│   ├── thrombin
│   ├── tyk2
```
- Dimer output energies are provided under `mbe2` and trimer output energies are provided under `mbe3`.

- All energies listed in the output .json files are in Hartrees.

## Poisson Boltzmann Surface Area Calculations
Output solvation energy files are arranged in the following layout

```
├── bace
│   ├── lig_13a
│   │   ├── 1
│   │   │   ├── complex_results.csv
│   │   │   ├── ligand_results.csv
│   │   │   ├── protein_results.csv
│   │   ├── 4
│   │   │   ├── complex_results.csv
│   │   │   ├── ligand_results.csv
│   │   │   ├── protein_results.csv
│   │   ├── 6
│   │   │   ├── complex_results.csv
│   │   │   ├── ligand_results.csv
│   │   │   ├── protein_results.csv
│   ├── ...
├── cdk2
├── jnk1
├── mcl1
├── p38
├── ptp1b
├── thrombin
├── tyk2
```
- Directories `1`, `4`, and `6` refer to the different solute dielectric constants
 
- `complex_results.csv` contains the solvation energies of the complex, `ligand_results.csv` contains the solvation energies of the ligand, `protein_results.csv` contains the solvation energies of the protein.

- All energy files listed in the output .csv files are in kJ/mol
