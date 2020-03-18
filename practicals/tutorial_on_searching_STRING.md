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

STRING (https://string-db.org) is a database of known and predicted protein-protein interactions. The interactions include direct (physical) and indirect (functional) associations; they stem from computational prediction, from knowledge transfer between organisms, and from interactions aggregated from other (primary) databases.

Data Sources
Interactions in STRING are derived from five main sources:

- Genomic Context Predictions	
- High-throughput Lab Experiments	
- (Conserved) Co-Expression	
- Automated Textmining	
- Previous Knowledge in Databases

Coverage
The STRING database currently (March 2020) covers 24'584'628 proteins from 5'090 organisms.

You will work with the following four genes in *Homo sapiens*:

**EGFR (EGFR_HUMAN)**
EGFR is an epidermal growth factor receptor and tyrosine kinase receptor that binds EGF factors to activate signal transduction cascades, converting external stimuli into cellular responses

**ERBB2 (ERBB2_HUMAN)**
ERBB2 is a tyrosine kinase receptor that is part of receptor complexes present on the cell surface. For its activation it seems to require the presence of a co-receptor. It is capable of binding neuregulins and regulates transcription in the nucleus

**ERBB3 (ERBB3_HUMAN)**
ERBB3 is a surface tyrosine kinase receptor for the binding of neuregulins. Activation is due to binding to neuregulin-1. It is involved in the regulation of myeloid cell differentiation.

**ERBB4 (ERBB4_HUMAN)**
ERBB4 is a tyrosine kinase receptor that binds EGF factors and neuregulines and is involved in proliferation and apoptosis. It acts in processes such as the development of heart tissue and the nervous system.

If you want to learn more about these genes, their biological function and the relation among them, you can use resources you know (Uniprot, PubMed, IntAct). 


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