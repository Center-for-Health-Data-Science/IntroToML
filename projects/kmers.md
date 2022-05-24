# Kmers in microbiome research
Microorganisms like bacteria and viruses live all around us.
Since human bodies are warm, moist and edible, they not only live _around us_, but also _inside us_ and _on us_.
The environment of microbes that we carry around us is called our _microbiome_.
The last decades, it has become clear that our microbiomes are deeply integrated with our bodies - as such,
[microbiomics has emerged as a rich field of research](https://www.nature.com/subjects/microbiome/nature).

### Microbiome data
Because most microorganisms can't be grown easily in the lab, modern studies on microbiomes make use of _shotgun metagenomics_,
where the DNA of the entire microbiome is extracted, then fragmented and sequenced.

This results in a large amount of sequences from a mix of organisms.
To reconstruct the microbiome, the researcher then has to determine the original source of, and relationship between, these sequences.

There are many approaches to this, but in this project, you will focus on _kmers_.

### Short kmers
A _k-mer_ or _kmer_ is a polymer composed of `k` units.
For example, when talking about DNA, a 4-mer is any piece of DNA consisting of 4 nucleotides, e.g. `AACT`.
The _kmer frequencies_ of a piece of DNA is the frequency of each continuous kmer subsequence in the sequence.
For example, for a 1000 bp sequence where `GGTG` occurs 19 times, there are $1000 - 4 + 1 = 997$ total 4-mers, and so `GGTG` has a frequency of $19 / 997 \approx 0.019$.

Kmer frequencies can be represented as a single numerical vector.
In this project you will be working with 4-mers. As there are $4^4 = 256$ different 4-mers from `AAAA` to `TTTT`, all 4-mer frequencies can be represented as a vector of length 256 where all elements are in $[0; 1]$ and the sum of all elements are 1.

[It has been known for decades](https://pubmed.ncbi.nlm.nih.gov/6583663/) that the frequencies of short kmers differ between sequences that originate from evolutionarily distinct groups.
There is no single comprehensive reason for this, although various factors such as DNA denaturation temperature, codon bias, common functional motifs, restriction endonucleases and others are thought to play a role.

Since numerical vectors are the bread and butter of machine learning,
the implication of this is that we can effectively represent and analyze long DNA sequences using their kmer frequencies.

## Task:
The file `data/kmers1.json` contains the 4-mer frequencies (TNF) from a sequences of microorganisms.

#### Use PCA to plot the first two components of the TNFs of all the sequences.
* How is the relationship between number of components and fraction variance explained?
  There are 4^4 = 256 features. Why does the relationship look like that?
* How many major groups of organisms are revealed using the PCA?
  There is not any objective answer to this: Inspect the PCA on different dimensions and pick out
  sequences you believe separate into distinct clusters, then label these as groups.

#### Build a classifier that, given a TNF from a sequence, predicts which of the major groups it belongs to.
* What is its accuracy?
* The other file `kmers2.json` contains TNF from microorganisms of different species, but the same major groups.
  test the accuracy of your classifier using validation data from `kmers1.json` and `kmers2.json`.
* Even if you use cross validation when using `kmers1.json`, your accuracy will be higher than using `kmers2.json`. Why?
