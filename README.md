# Ti-uniaxial-compression
Data supporting molecular-dynamics simulations of uniaxial compression of crystalline HCP titanium. Includes input files and analysis outputs for investigating system-size effects on the deformation processes.

Titanium structures of seven different model sizes and four different strain rates were used in the simulations.

# Files

- Generating_initial_Ti_models.txt - information about how the different Ti models are constructed
- Ti-equilibration.in - NPT MD equilibration at 300 K and 0 bar
- Ti-compression.in - uniaxial compression in z-direction
- Deformation - stress-strain analysis 
- PTM - structural phase analysis using Polyhedral Template Matching
- DXA - dislocation density analysis using Dislocation Extraction Algorithm
- library.meam, Ti.meam - MEAM interatomic potential parameters for Ti

# Software

- Initial structure files are built with [ATOMSK](https://atomsk.univ-lille.fr/)
- MD simulations are performed with [LAMMPS](https://www.lammps.org/)
- PTM and DXA analysis are performed with [OVITO](https://www.ovito.org/)

# Usage

To build the initial structures of Ti models run the following command line in your terminal by choosing the appropriate replication:

atomsk --create hcp 2.95 4.68 Ti orient [10-10] [1-210] [0001] -duplicate N N N TiN.lmp 

First run equilibration. Update "TiX.lmp" in the "Ti-equilibration.in" input file to match the corresponding model size.

Then run compression. Change the applied strain rate in the "Ti-compression.in" input file, by adjusting the following line (all other parameters are calculated automatically):

variable srate equal 1.0e9    # 1.0e8, 5.0e8, 1.0e9, 1.0e10

# Notes

Each deformation output file contains the values of strain and of all three stress components. 
Only the stress in the loading direction (z-axis) is used for the analysis. The lateral components were recorded to monitor the loading conditions during the simulation.

The MEAM potential used for the MD simulations is from: Kim, Lee, and Baskes, Phys. Rev. B 74, 014101 (2006). https://doi.org/10.1103/PhysRevB.74.014101


# Citation

The data are associated with the study currently in the ArXiv: F. Safari and K. Konstantinou*, arXiv (2026), arXiv: 2606:28155. https://arxiv.org/abs/2606.28155

Will be updated accordingly upon journal publication.
