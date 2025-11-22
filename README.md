# MULTIPLE-SEQUENCE-ALIGNMENT
SEQUENCE ALIGNMENT
# 🧬 Multiple Sequence Alignment (MSA) and Phylogenetic Analysis with Biopython

## 📝 Overview

This repository contains a Jupyter Notebook (`MSA WITH BP.ipynb`) that demonstrates a complete workflow for performing **Multiple Sequence Alignment (MSA)** using the external tool **Clustal Omega** and subsequently analyzing the results using the **Biopython** library.

The analysis includes generating the alignment, calculating sequence conservation, visualizing conservation using a heatmap, and constructing/visualizing the guide tree derived from the alignment.

## 🚀 Project Steps

The notebook follows these key bioinformatics steps:

1.  **Tool Installation**: Installs the required Python library (`biopython`) and the external MSA tool (`clustalo`).
2.  **Data Preparation**: Three sample protein sequences (`seq1`, `seq2`, `seq3`) are defined, encapsulated as `SeqRecord` objects, and written to a FASTA file (`input_sequences.fasta`).
3.  **Multiple Sequence Alignment (MSA)**: **Clustal Omega** is executed via the Python `subprocess` module to align the sequences and save the result to `aligned_output.fasta`.
4.  **Alignment Display**: The aligned sequences are read back into Biopython using `AlignIO.read()` and displayed.
5.  **Format Conversion**: The alignment is saved in the **Clustal format** (`aligned_output.aln`).
6.  **Conservation Identification (Textual)**:
    * The script iterates through each column (position) of the alignment.
    * It uses `collections.Counter` to check if all residues in a column are identical.
    * Conserved positions are printed with an asterisk (`*`) marker beneath the alignment for clear visualization.
7.  **Conservation Visualization (Heatmap)**:
    * **Conservation scores** (ranging from 0.0 to 1.0) are calculated for every position based on the frequency of the most common residue in that column.
    * A **heatmap** is generated using `matplotlib` and `seaborn` to visually represent the conservation score across the entire sequence length.
8.  **Phylogenetic Tree Generation**:
    * **Clustal Omega** is re-run to specifically output the **guide tree** (unrooted tree used internally for alignment construction) in a Newick file (`alignment.dnd`).
    * The tree is read using `Bio.Phylo.read()` and visualized graphically using `Phylo.draw()`.

## 🛠️ Requirements and Setup

### Prerequisites

To successfully run the script, both the Python library and the external command-line tool must be installed:

* **Python Libraries**:
    ```bash
    !pip install biopython matplotlib seaborn numpy
    ```
* **External Tool**:
    ```bash
    !apt-get install -y clustalo
    ```
    *Note: This command is suitable for Debian/Ubuntu-based environments like Google Colab or typical Linux servers.*

### Input Data

The script **generates its own input sequences** but requires the **Clustal Omega** tool to operate on the generated FASTA file (`input_sequences.fasta`).

The script produces the following key files:

| Filename | Format | Content |
| :--- | :--- | :--- |
| `input_sequences.fasta` | FASTA | The three unaligned protein sequences. |
| `aligned_output.fasta` | FASTA | The final MSA, used for analysis. |
| `aligned_output.aln` | CLUSTAL | The MSA saved in CLUSTAL format. |
| `alignment.dnd` | Newick | The phylogenetic guide tree file. |
