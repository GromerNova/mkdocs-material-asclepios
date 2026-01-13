# Asclepios General Purpose 📄

Asclepios General Purpose class is the communication channel between the User and the KNIME Analytics Platform. This class contains the file loader and file writer nodes.  

#### File Loader

The node is used to load the file of the ligand (or ligands) and proteins in the workflow. The file can contain one or multiple ligands if the user is employing the workflow for virtual screening. It can also be employed for loading common file types employed in Cheminformatics and medicinal Chemistry. Common formats include SDF/MOL, MOL2, PDB and XYZ files. GAMESS output files are also supported. The node can be implemented to load specific file formats required for specialized nodes such as the Asclepios AMBER nodes. 

The advantage of SDF/MOL files is that they can contain thousands of structures, allowing the user to perform virtual screening and can be read/saved by most visualization software. The PDB file format is the most commonly used format for saving protein structural information.

Output:

| In-ports | Filename |  Content |
| -------- | -------- | -------- |
| port 0   |   `String`  |  `String`  |






