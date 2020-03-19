---
title: Serching Protein Interactions in the STRING database
authors:  Allegra Via 
based on: STRING documentation 
minutes: 30
---

------------

> ## Learning Outcomes
> Learners will be able to:
> * use STRING to find interaction partners of an input protein of interest
> * visualise the interaction network of input proteins 
> * download the results of their search 
> 
> ## The aim of the task
> The aim of this tutorial is to give learners the chance to explore the STRING database and practice searches.

------------
## Background

### The STRING database

[STRING]((https://string-db.org)) (Search Tool for the Retrieval of Interacting Genes/Proteins) is an online database and search tool for retrieval of interactions involving proteins; interactions include direct (physical) and indirect (functional) associations between proteins; they stem from computational prediction, from knowledge transfer between organisms, and from interactions aggregated from other (primary) databases.
Data are derived from five main sources:

- genomic analysis (Genomic Context Predictions)
- high-throughput lab experiments
- (conserved) coexpression experiments
- previous knowledge from public text collections (OMIM, PubMed) - via automated text minind
- Previous Knowledge in Databases

It is a secondary database, that is a curated database consisting of data derived from analysis of DNA sequences, protein sequences, and structures (from resources like DIP, KEGG, GO and BioGRID).
The database is collectively curated by EMBL, CPR and KU (Copenhagen), SIB, TUD (Dresden), and UZH (Zurich); it covers 9643763 proteins from 2031 different organisms.
Online data search and most flat files are free under Creative Commons License, but the full database and resources are released under license requirements for commercial uses; institutions can ask for customized data collections behind payment.

It has two sister projects based on the data contained in STRING:
• STITCH, a database of chemical-protein interactions
• EggNOG, a database for functional annotation of orthologous groups.


#### Coverage
The STRING database currently (March 2020) covers 24'584'628 proteins from 5'090 organisms.


### How to do perform a search using STRING

From the main page of STRING, you can perform a search:

- by name
- by sequence
- by multiple names
- by multiple sequences

In the first case, the user can insert the common name of the protein of interest, its scientific name or any accession number from other databases. 

In the second case, a sequence in FASTA format is required. 

In both instances, the search returns a network of proteins that are involved in primary AND secondary interactions with the query; the visualized network is a summary network by default and emphasizes with different colors the different pieces of evidence that support each specific interaction (for example experimental proof, inference by homology, presence in literature etc). 

By clicking different buttons at the bottom of the image, specific networks and relations based on phylogenetics can be highlighted; the buttons indicated by plus and minus symbols allow the user to focus on smaller or larger networks by adding or eliminating nodes, based on a ranking that represents the cumulative degree of confidence that each specific PPI actually exists. 

The multiple searches allow instead to define real and putative interactions limited to the set of proteins fed to the system by the user. There is also the possibility to search for COGs (clusters of orthologous groups, that is a phylogenetic classification of similar proteins in different species) instead of simple protein interactions. 

For every search performed in any chosen visualization of the network, in a box under the image a full explanation of what you are viewing is given, together with a set of variables that can be modified in order to customize the network and highlight specific contents. Clicking on the name of an interacting partner redirects to a specific page where info about identity, function and protein sequence are given, together with their UniProt accession number and external links to NCBI, Ensembl, KEGG, UniProt, the Yeast Genome Project and many other databases.

You will work with the following four genes in *Homo sapiens*:

**EGFR (EGFR_HUMAN)** <br>
EGFR is an epidermal growth factor receptor and tyrosine kinase receptor that binds EGF factors to activate signal transduction cascades, converting external stimuli into cellular responses

**ERBB2 (ERBB2_HUMAN)** <br>
ERBB2 is a tyrosine kinase receptor that is part of receptor complexes present on the cell surface. For its activation it seems to require the presence of a co-receptor. It is capable of binding neuregulins and regulates transcription in the nucleus

**ERBB3 (ERBB3_HUMAN)** <br>
ERBB3 is a surface tyrosine kinase receptor for the binding of neuregulins. Activation is due to binding to neuregulin-1. It is involved in the regulation of myeloid cell differentiation.

**ERBB4 (ERBB4_HUMAN)** <br>
ERBB4 is a tyrosine kinase receptor that binds EGF factors and neuregulines and is involved in proliferation and apoptosis. It acts in processes such as the development of heart tissue and the nervous system.

If you want to learn more about these genes, their biological function and the relation among them, you can use resources you already know (Uniprot, PubMed, IntAct). 


### Searching STRING
Go to the [STRING](https://string-db.org) database.

#### Searching STRING with a single protein
Search EGFR in STRING, specifying *Homo sapiens* as organism.
You will be presented with a list of entries related to EGFR. You have to select one and then click on CONTINUE.
If you search STRING with EGFR_HUMAN (Uniprot ID), you will directly get the results. 

**Q1: How many interaction partners can you see?**

Click on "Legend".

**Q2: What is the meaning of the different colours of the nodes (proteins)?
**

**Q3: What is the meaning of the different colours of the edges (interactions)?**

Go to "Settings" and exclude unreliable interactions (only keep "Experiments" and "Databases" interaction sources active).

**Q4: How many interaction partners can you see now? **

Try the "+More" button. 

**Q5: how much do you have to increase the network size (= number of interactors) in order to see ERRB2 and ERRB3 to appear in the network?**

Browse STRING Help and, from there, the Documentation. 

**Q6: Try to find out what is the "confidence score" and what is the minimum required interaction score for high scoring interactions.**

#### Searching STRING with multiple proteins

Do a research on STRING with all four proteins together:

- EGFR
- ERBB2
- ERBB3
- ERBB4

Or:

- EGFR_HUMAN
- ERBB2_HUMAN
- ERBB3_HUMAN
- ERBB4_HUMAN

try to understand if the proteins interact with each other and how (ie try to characterise the type of interaction).

**Q7: With which experiments were the interactions identified?**

**Q8: Are the interactions reliabile?**

**Q9: Do the four proteins form a complex? Or do they form transient interactions?**

**Q10: What is the confidence score of these interactions?**

**Q11: What happens to the network if you set to 0.9 the minimum score for displaying interactions?**

Try the "+More" button. 