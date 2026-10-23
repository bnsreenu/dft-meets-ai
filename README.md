# DFT meets AI

Companion code for the DigitalSreeni video on density functional theory (DFT) and pretrained AI models.

The notebook does the same job twice, with traditional DFT and with a machine-learned interatomic potential, and compares them.

Link to video: (add link after upload)

## What is in the notebook

**Part 1: ethanol**
- Traditional DFT with PySCF (B3LYP with dispersion correction, def2-SVP basis): geometry relaxation, forces, timing.
- The same molecule with MACE-OFF23, a pretrained AI potential.
- Comparison of structure, forces, energy differences, a torsion scan, cost with growing molecule size, and a short molecular dynamics run.
- Where the model fails: elements outside its training set.

**Part 2: aluminum nitride (AlN)**
- Small clusters (AlN and Al2N2): unrestricted DFT in several spin states against MACE-MP-0.
- Vibrational frequency check for true minima.
- Bulk AlN: wurtzite, zincblende and rocksalt with MACE-MP-0, compared with literature lattice constants.

## How to run

Use Google Colab. PySCF does not run natively on Windows (use WSL or Linux if you want to run locally).

1. Open `dft_vs_ai.ipynb` in Colab.
2. Optional: Runtime > Change runtime type > GPU. DFT runs on the CPU, and the AI model uses the GPU if there is one.
3. Run the install cell, then restart the runtime if asked:

   pip install -q --prefer-binary pyscf pyscf-dispersion ase mace-torch rdkit

4. Run all cells. Part 2 takes the longest because of the DFT relaxations and frequency checks. Set `DFT_FREQUENCIES = False` in the settings cell to skip the slowest part.

Outputs (figures, tables and a summary JSON) are saved to `outputs/dft_vs_ai/`.

## Models and licenses

| Model | Covers | License |
|---|---|---|
| MACE-OFF23 | Organic molecules, 10 elements | Academic Software License (non-commercial) |
| MACE-MP-0 | Materials, 89 elements | MIT |

Please check each license before using a model commercially.

## Notes and limits

- The DFT level used here (B3LYP, small basis) differs from the level the AI models were trained on, so part of any disagreement is a difference in level of theory.
- The cluster results depend on the functional, basis set, starting structures and the spin states tried. Treat them as results at this level of theory.
- Bulk AlN is compared with literature values, not with periodic DFT.
- Skala (Microsoft's learned functional) is mentioned in the video and notebook but not run.

## Author

Sreenivas Bhattiprolu, DigitalSreeni
YouTube: DigitalSreeni | digitalsreeni.com
