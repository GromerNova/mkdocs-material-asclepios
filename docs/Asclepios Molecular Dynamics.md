# Asclepios Molecular Dynamics ⚙️

Asclepios Preparator class is a collection of nodes for pre-molecular dynamics simulation procedure. Currently Asclepios preparator class supports two molecular dynamics protocols, employed by GROMACS[^1] and OpenMM[^2].   


#### Antechamber Plus

Asclepios Antechamber Pluse node includes the ligand parameter preparation tool Antechamber, provided by AMBER. The node employs Antechamber to assign partial atomic charges with the AM1-BCC methodology. Antechamber[^3]  utilizes the GAFF and GAFF2 force fields[^4] to assign the parameters and the topology of a chemical molecule that will be used as a ligand in complex witha biological macromolecule. 

Input:

| In-ports | Filename | Content |
| -------- | -------- | -------- |
| port 0   |   `String`  |  `mol2`  |

Output:

| In-ports | Filename |  Content |
| -------- | -------- | -------- |
| port 0   |   `String`  |  `mol2`  |
| port 1   |   `String`  | `frcmod` |


#### Amber System Prep

Asclepios Amber System Prep node facilitates the generation of the files that are required torun an MD simulation using the AMBER software[^5]. The files generated include information for the size and the type of atoms in the system (e.g. protein-ligand complex) to be simulated (parameter/topology file) and the Cartesian coordinates. 

Input:

| In-ports | Content (Ligand's molecular configuration) |
| -------- | -------- |
| port 0   |  `String` `mol2`  |

| In-ports | Content (Ligand's AMBER topology)|
| -------- | -------- |
| port 1 (optional)   | `String` |

| In-ports | Content (Receptor)|
| -------- | -------- |
| port 2   |  `String` `pdb` |


Output:

| In-ports | Filename |  Content |
| -------- | -------- | -------- |
| port 0   |   `String`  |  `String`  |

#### MD Simulation (OpenMM)

The node is built to fully implement the OpenMM software for Molecular Dynamics (MD) simulations. It offers the user the ability to apply the conditions required for the simulation such as the length of the MD (ns), the temperature (K) and pressure (atm) as long as other available options as presented in the dialogue options.

Input:

| In-ports | Filename | Content |
| -------- | -------- | -------- |
| port 0   | `String` | `String` |

Output:


| Out-ports | Filename | XTC Content | PDB Content |
| -------- | -------- | -------- | -------- |
| port 0   | `String` | `Binary` | `pdb`    |

[^1]: Van Der Spoel, D., Lindahl, E., Hess, B., Groenhof, G., Mark, A.E. and Berendsen, H.J.C. (2005), GROMACS: Fast, flexible, and free. J. Comput. Chem., 26: 1701-1718. https://doi.org/10.1002/jcc.20291

[^2]: Peter Eastman, Raimondas Galvelis, Raúl P. Peláez, Charlles R. A. Abreu, Stephen E. Farr, Emilio Gallicchio, Anton Gorenko, Michael M. Henry, Frank Hu, Jing Huang, Andreas Krämer, Julien Michel, Joshua A. Mitchell, Vijay S. Pande, João PGLM Rodrigues, Jaime Rodriguez-Guerra, Andrew C. Simmonett, Sukrit Singh, Jason Swails, Philip Turner, Yuanqing Wang, Ivy Zhang, John D. Chodera, Gianni De Fabritiis, and Thomas E. Markland
The Journal of Physical Chemistry B 2024 128 (1), 109-116
DOI: 10.1021/acs.jpcb.3c06662

[^3]: [Antechamber Plus](https://ambermd.org/doc12/Amber23.pdf)

[^4]: Wang, J., Wolf, R.M., Caldwell, J.W., Kollman, P.A. and Case, D.A. (2004), Development and testing of a general amber force field. J. Comput. Chem., 25: 1157-1174. https://doi.org/10.1002/jcc.20035

[^5]: [AMBER](https://ambermd.org/)

## Workflows

??? example "Ligand's topology and molecular configurations files."

    ![Load a set of lignads](assets/preparator/preparator_scenario1_1.png){ align=left }

    <center>

    | Scenario  | Workflow (Nodes involved) | Classes |
    | -------- | -------- | ---------------- |
    | Ligand's topology and molecular configurations files. | [File Loaders {`sdf`}, Transformer {`sdf` &rarr; `mol2`} &rarr; Antechamber Plus]  | [📄](Asclepios General Puprose.md "Asclepios General Puprose") [🧬](Utilizer.md "Asclepios Utilizer")[⚙️](Asclepios Molecular Dynamics.md "Asclepios Molecular Dynamics") |

    Download workflow [:material-download:](../assets/preparator/preparator_scenario1.knwf)

    </center>

??? example "The extra utility of Utilizer applied for Amber system preparation."

    ![Load a small molecule and the receptor](assets/preparator/scenario3.png){ align=left }

    <center>

    | Scenario  | Workflow (Nodes involved) | Classes |
    | -------- | -------- | ---------------- |
    | Molecular docking | Asclepios File Loader {`SDF`,`Mol2`} &rarr; Asclepios RxDock| [📄](Asclepios General Puprose.md "Asclepios General Puprose") [💊](Medic.md "Asclepios Molecular Docking") |
    | Ligand preparation | Asclepios AddHydrogens &rarr; Transformer {`SDF` &rarr; `Mol2`} &rarr; Antechamber Plus &rarr; Asclepios Amber System Prep  | [📄](Asclepios General Puprose.md "Asclepios General Puprose") [🧬](Utilizer.md "Asclepios Utilizer")[⚙️](Asclepios Molecular Dynamics.md "Asclepios Molecular Dynamics") |
    | Preotein preparation |Transformer {`Mol2` &rarr; `PDB`} &rarr; Antechamber Plus &rarr; Asclepios Amber System Prep  | [📄](Asclepios General Puprose.md "Asclepios General Puprose")[🧬](Utilizer.md "Asclepios Utilizer")[⚙️](Asclepios Molecular Dynamics.md "Asclepios Molecular Dynamics") |

    Download workflow [:material-download:](../assets/preparator/preparator_scenario2.knwf)

    </center>










