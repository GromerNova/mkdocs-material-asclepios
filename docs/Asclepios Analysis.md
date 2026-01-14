# Asclepios Analysis 🔍

Asclepios Analyzer class is a collection of nodes for data analysis and data visualization. The goal is to provide extra information about the specific chemical structure or to analyze a trajectory accordingly.

#### Molecule Checker

Asclepios Molecule Checker offers a data curation protocol powered by the ChEMBL data curation pipeline[^1], which was used to create a molecular database widely used for bioactive small molecules. By adopting this approach, Asclepios Checker enhances Asclepios' drug discovery capabilities, providing users with an efficient and accurate method for curating and processing bioactive data. This integration allows for improved consistency, reliability, and the ability to leverage ChEMBL’s rich dataset in drug discovery workflows.

Input:

| In-ports | Filename | Content (DB)|
| -------- | -------- | -------- |
| port 0   | `String` | `sdf` `mol`  `String` |

Output:

| Out-ports | Filename | Content (LowQ) | Issue | Scoring | IDs |
| -------- | -------- | -------- | -------- | -------- | -------- |
| port 0   | `String` | `mol` | `String` | `Integer` | `Integer` |

| Out-ports | Filename | Content (HighQ) | IDs |
| -------- | -------- | -------- | -------- |
| port 1   | `String` | `mol` | `Integer` |

| Out-ports | Filename | Content (LowQ or HighQ or DB) |
| -------- | -------- | -------- |
| port 2   | `String` |  `sdf` | 


#### PDB Summary
The PDB summary exporter is a bioinformatics utility designed to extract and export concise summary information from Protein Data Bank [^2] in a Table format. It streamlines the process of gathering essential structural and bibliographic data from 3D macromolecular structure files. 

Input:

| In-ports | Filename | Content |
| -------- | -------- | -------- |
| port 0   | `String` | `pdb` `String` |

Output:

| Out-ports | Filename | Rvalue free | Rvalue work | Resolution | Rvalue observed |
| -------- | -------- | -------- | -------- | -------- | -------- |
| port 0   | `String` | `Double` | `Double` | `Double` | `Double` |

#### Dock Result Viewer
Asclepios Docking Reader is a useful toolkit to retrive the information about the quantitative data of a specific molecular docking process via RxDock node such as ligand's docking score of its specific pose. In case of selecting extra ranking methods the corresponding optional port are activated.

Input:

| In-ports | Filename | Content |
| -------- | -------- | -------- |
| port 0   | `String` | `sdf` `mol` `String` |


Output:

| Out-ports | Filename | Content | Score | Score Inter-molecular | Score Inter-Polar-molecular | Score Intra-molecular |
| -------- | -------- | -------- | -------- | -------- | -------- |  -------- |
| port 0   | `String` | `mol` | `Double` | `Double` | `Double` | `Double` |

| Out-ports | Filename | Content | Score | Score Inter-molecular | Score Inter-Polar-molecular | Score Intra-molecular |
| -------- | -------- | -------- | -------- | -------- | -------- | -------- |
| port 1 (optional)   | `String` | `mol` | `Double` | `Double` | `Double` | `Double` |

| Out-ports | Filename | Content | Score | Score Inter-molecular | Score Inter-Polar-molecular | Score Intra-molecular |
| -------- | -------- | -------- | -------- | -------- | -------- | -------- |
| port 2  (optional) | `String` | `mol` | `Double` | `Double` | `Double` | `Double` |


#### MM-PB/GBSA Analysis
The node carries out binding affinity calculation with the MolecularMechanics -Poisson-Boltzmann surface area (MM-PBSA) or Molecular Mechanics -Generalized Born Surface Area (MM-GBSA) method. Both methods calculate the relevant binding affinity taking into account the desolvation penalty. MM-GBSA is preferred to MM-PBSA due to its low computational cost [^3].

Input:

| In-ports | Filename | Content |
| -------- | -------- | -------- |
| port 0   | `String` | `String` |

Output:

| In-ports | Filename | Content |
| -------- | -------- | -------- |
| port 0   | `String` | `String` |

[^1]: Bento, A.P., Hersey, A., Félix, E. et al. An open source chemical structure curation pipeline using RDKit. J Cheminform 12, 51 (2020). https://doi.org/10.1186/s13321-020-00456-1
[^2]: [RCSB PDB](https://www.rcsb.org/)
[^3]: https://ambermd.org/tutorials/advanced/tutorial3/

## Workflows

??? example "Check molecular characteristics during data type transformations."

    ![Load a set proteins for docking preparation (high-throughput screening)](assets/analyzer/analyzer_scenario1.png){ align=left }

    <center>

    | Scenario  | Workflow (Nodes involved) | Classes |
    | -------- | -------- | ---------------- |
    | Check ligand following a `SDF` transformation  | [File Loader &rarr; Transformer {`PDBQT`&rarr;`SDF`} &rarr; Generate 2D3D &rarr; Molecule Checker] | [📄](Asclepios%20General%20Purpose.md "Asclepios General Puprose") [🧬](Asclepios%20Utilizer.md "Asclepios Utilizer")  [🛠️](Asclepios%20Builder.md "Asclepios Builder") [🔍](Asclepios%20Analysis.md "Asclepios Analysis") |
    | Check ligand after an intermidiate `PDB` transformation | [File Loader &rarr; Transformer {`PDBQT`&rarr;`PDB`} &rarr; Transformer {`PDB`&rarr;`SDF`} &rarr; Generate 2D3D &rarr; Molecule Checker]  |  [📄](Asclepios%20General%20Purpose.md "Asclepios General Puprose") [🧬](Asclepios%20Utilizer.md "Asclepios Utilizer")  [🛠️](Asclepios%20Builder.md "Asclepios Builder") [🔍](Asclepios%20Analysis.md "Asclepios Analysis") |

    Download workflow [:material-download:](../assets/analyzer/analysis_scenario1.knwf)

    </center>








[^1]: Bento, A.P., Hersey, A., Félix, E. et al. An open source chemical structure curation pipeline using RDKit. J Cheminform 12, 51 (2020). https://doi.org/10.1186/s13321-020-00456-1











