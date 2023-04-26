# Predicting a residue's secondary structure

## The task

One long-standing task in structural bioinformatics has been predicting the secondary structure ($\alpha$-helices, $\beta$-strands, turns, unstructured regions, etc.) of proteins from their primary amino acid sequence.

![figure_alpha_helix](figures/figure_ss.pdf)

This issue usually boils down to a classification problem where the secondary structure of a single residue is inferred from the sequence context (the flanking residues) on both sides of the residue of interest.

In this project, your task is to build a classifier that predicts the secondary structure of a residue by considering its context and evaluating its performance.

## The dataset

The complete dataset comprises roughly 5400 protein sequences for which secondary structure assignments were obtained using the [DSSP](https://swift.cmbi.umcn.nl/gv/dssp/DSSP_3.html) algorithm [^Kabsch and Sander, 1983].

DSSP assigns per-residue secondary structures based on the patterns of hydrogen bonding observed for the residue and the residue's geometrical features.

Both the protein sequences and their per-residue DSSP assignments are available as FASTA files:

* `sequences.fasta` contains the protein sequences.
* `secstructs.fasta` contains the secondary structure assignments.

You can load the FASTA file and split the datasets into training and testing sets in a way similar to how it was done in the TSS exercise.

### Dataset generation

This section is not strictly necessary to complete the project, but it is recommended to read it if you want to figure out where the dataset comes from and why it has been generated this way 😉

The dataset was obtained from the [SCOP](https://scop.mrc-lmb.cam.ac.uk/) database [^Andreeva et al., 2007].

SCOP provides a hierarchical classification of proteins' three-dimensional structures into `Protein Types`, `Protein Classes`, `Folds`, `Superfamilies`, `Families`, and `Domains`. `Protein Types` are the broadest structural classes, while `Domains` provide the finest-grained classification. For each `Domain`, SCOP provides a "representative" structure. For example, for each `Family`, `Superfamily`, and other higher levels in the hierarchy, multiple representative structures are available (since each representative structure is associated with a single `Domain`, and each `Family`, `Superfamily`, etc., contains several `Domains`).

Each representative structure is defined in terms of its ID in the Protein Data Bank (PDB ID) and the chain in the structure representing the `Domain` of interest (the chain specification is necessary since the selected structure may easily be a multimer).

For our dataset, we selected, for each SCOP `Family`, the "best" representative structure among the structures of the `Family`'s domains. The "best" structure was the one with the highest resolution and, in case of ties, the one most recently deposited in the Protein Data Bank. Then, the structure's file was downloaded from the Protein Data Bank, and the chain of interest was extracted. Then, DSSP was run on the chain's structure to obtain the secondary structure assignments.

**Question**: why do you think the dataset was generated from a structural classification? What could be the advantages of having structurally diverse proteins in our dataset?

## References

[^Andreeva et al., 2007]: Andreeva, Antonina, et al. "Data growth and its impact on the SCOP database: new developments." *Nucleic acids research* 36.suppl_1 (2007): D419-D425.
[^Kabsch and Sander, 1983]: Kabsch, Wolfgang, and Christian Sander. "Dictionary of protein secondary structure: pattern recognition of hydrogen‐bonded and geometrical features." *Biopolymers: Original Research on Biomolecules* 22.12 (1983): 2577-2637.

