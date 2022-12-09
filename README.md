# DTP project 2022

Data files for DTP Bioinformatics hackathon project, December 2022.  

The aim of the project is to investigate the following hypothesis:

**Hypothesis**: the more prevalent a resistance gene is in *Escherichia coli*, the fewer restriction targets it should have in its sequence. 

### Background

Restriction-modification systems are the most prevalent form of 'defense system' that bacteria have against incoming DNA from the wider pangenome: bacterial viruses (phage) and plasmids. R-M systems are present in 83% of prokaryotic genomes, nearly double the rate of the next most abundant defense system, CRISPR-Cas. The restriction enzymes chop up incoming foreign DNA that lacks the correct methylation pattern (the addition of a methyl group that stops ut binding and chopping up the DNA). 

The most abundant type of R-M system are Type II systems. Type II R-M systems target short stretches of DNA of 4-8bp long, which are 'palindromic' in DNA terms (e.g. GAATTC which when reversed and complemented - G becomes C, A becomes T etc. - is identical to itself). Bioinformatic analysis confirms that both phages, plasmids, and bacterial chromosomes are under selective pressure to avoid these short palindromes in their sequence - they have fewer than would be expected by chance.

In this project, you will investigate the occurrence of restriction targets in antimicrobial resistance (AMR) genes in *Escherichia coli* (*E. coli*). 

## Dataset 

Data are provided from [CARD](https://card.mcmaster.ca/), a database of AMR genes. 

Within `data` directory, the following data files have been provided

* `CARD_Escherichia_coli_AMR_gene_prevalence.tsv` - prevalence information on AMR genes within *Escherichia coli*: how many genomes have the AMR gene?
* `CARD_Escherichia_coli_nucleotide_AMR_genes.fasta` - nucleotide fasta file of AMR genes (only those within *Escherichia coli*): the actual sequences of the AMR genes. 
* `restriction_targets_genome_prevalence.txt` - table of the targets of Type II R-M systems which are 6-bp long with their prevalence in n=1611 *Escherichia coli* genomes: how prevalent are Type II R-M systems targeting each target?

For the purposes of this project I have selected out only resistance genes that have been detected by a [protein homolog model](https://card.mcmaster.ca/ontology/40292): "Protein Homolog Models apply to all genes that confer resistance through their presence in an organism, such as the presence of a beta-lactamase gene on a plasmid." I have also selected only restriction targets of length k=6. 

## Suggested tasks

Primary analysis:

* Write a script to count occurrences of short strings ('k-mers') of a given length `k` in an input sequence
* Apply this script to the AMR genes in the `.fasta` file
* Look at occurrences of the restriction targets across genes
* Test if patterns are consistent with the hypothesis

For testing, you will need to think about the independence (or not) of the genes you are testing. 

Secondary analysis (only if complete primary!):

* Use [R'MES](https://forgemia.inra.fr/sophie.schbath/rmes/-/blob/master/doc/rmes3.1.0cmake.userguide.pdf) to calculate exceptionality scores for k-mers
* Look at exceptionality scores of the restriction targets
* Test if patterns are consistent with the hypothesis

