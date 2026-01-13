# Workflows

??? example "Load a set of proteins"

    ![Load a set of proteins](assets/scenario1.png){ align=left }

    <center>

    | Scenario  | Workflow (Nodes involved) | Classes |
    | -------- | -------- | ---------------- |
    | Load a set of proteins | [File Loader, Get PDB]  | [:dna:](Utilizer.md) |

    </center>

??? example "Load a protein for docking preparation"

    ![Load a protein for docking preparation](assets/scenario2.png){ align=left }

    <center>

    | Scenario  | Workflow (Nodes involved) | Classes |
    | -------- | -------- | ---------------- |
    | Load a protein for docking preparation | [File Loader, Utilizer] | [:dna:](Utilizer.md) |

    </center>

??? example "Load a set proteins for docking preparation (high-throughput screening)"

    ![Load a set proteins for docking preparation (high-throughput screening)](assets/scenario3.png){ align=left }

    <center>

    | Scenario  | Workflow (Nodes involved) | Classes |
    | -------- | -------- | ---------------- |
    | Load a set proteins for docking preparation (high-throughput screening) | [File Loader, Utilizer] | [:dna:](Utilizer.md) |

    </center>

??? example "Load a protein and fix the structure (ie. adding missing residues and removing water molecules)"

    ![Load a protein and fix the structure (ie. adding missing residues and removing water molecules)](assets/scenario4.png){ align=left }

    <center>

    | Scenario  | Workflow (Nodes involved) | Classes |
    | -------- | -------- | ---------------- |
    | Load a protein and fix the structure (ie. adding missing residues and removing water molecules)| [File Loader, PDBFixer, Utilizer]  | [:dna:](Utilizer.md) |

    </center>

    <div class="annotate" markdown>

    > blue-colored representation (1) and the grey oval area sketced the adding residues.

    </div>

    1.  PDB fixed





