---
layout: topic
title: Protein-protein interaction prediction using docking
author: Allegra Via  
based on: a practical by D. Raimondo
minutes: 60 (excluding ClusPro run)
ClusPro run: up to a few hours
---

> Unless you can organise your teaching with a long break between the ClusPro job submission and the analysis of results, I strongly suggest you generate the solutions in advance and provide them to the students. In order to use ClusPro, you can generate an account (advised). However, you can also run a job without being registered. The procedure to request an account is described in this tutorial.

---
> ## Learning Objectives
>
> * Introduce the biological context of the MKK7-Gadd45B interaction
> * Identification of restraints to limit docking conformations
> * Predict the MKK7-Gadd45B complex using ClusPro
> * Explore ClusPro results


# Protein-protein interaction prediction using docking

In this tutorial you are going to predict and analyse the structural complex between the human MKK7 and Gadd45B protein structures. Before we start using bioinformatics tools and resources, we have to learn something about these two proteins and their interaction. 

> Studying the literature and having a good grasp on the biological problem you are dealing with, is essential to take full advantage of predictions. Predictions are simply predictions until you don't analyse them in the light of the knowledge deriving from wet experiments.

##The biological background: MKK7 and Gadd45B

NF-kB/Rel factors control programmed cell death, and this control is crucial to oncogenesis, cancer chemoresistance, and antagonism of tumor necrosis factor (TNF) α-induced killing. With TNF, NF-kB-mediated protection involves suppression of the c-Jun-N-terminal kinase (JNK) cascade, and **Gadd45β**, a member of the Gadd45 family, was identified as a pivotal effector of this activity of NF-kB. Inhibition of TNFα-induced JNK signaling by Gadd45β depends on direct targeting of the JNK kinase, **MKK7/JNKK2**. The mechanism by which Gadd45β blunts MKK7, however, is unknown (Papa et al, JBC 2007, Tornatore et al, JMB 2008).

(Papa et al, JBC 2007) modelled the interaction between Gadd45β and MKK7 and validated the model through a number of complicated mutagenesis experiments.

The formation of the Gadd45β-MKK7 complex **enables insertion of the Gadd45β acidic loop 1 into the MKK7 catalytic pocket**, where this could engage in H-bonds and polar interactions with MKK7 Lys149 and other residues normally binding to the three-phosphate group of ATP. This engagement of the MKK7 ATP-binding site by Gadd45β loop 1 seems to prevent access of the kinase to ATP.
Therefore, **the Gadd45β-MKK7 complex formation inhibits MKK7 by preventing it from binding ATP**.
They also found that residues within putative Gadd45β acidic loops 1 and 2 – i.e. **Glu65, Glu66 and Glu113** – directly contact basic residues within the catalytic pocket of MKK7 – i.e **Lys149, Lys157 and Arg162**. In particular, as shown in the figure below (figure 9C from Papa et al. 2007) inter chain hydrogen bonds form between the following residues:

MKK7 residue | Gadd45β residue
:-------------:|:----------------:
K149         | E65
R162         | E66
K157         | E113


<img src= "img/mkk7_gadd45B.jpg" width="50%">
Figure 9C from Papa et al.2007



##Sharpening your pencils

Before starting the actual study of the interaction, we need to do a number of things to get ready.

1. Build the homology model of Gadd45β
2. Retrieve the crystal structure of the most suitable conformation for MKK7
3. Identify appropriate restraints to limit the number of docking conformations

Once we have collected these data, we will be ready to use [ClusPro](http://cluspro.bu.edu/home.php)to predict the MKK7-Gadd45β complex.

```
Note:
In the following you will need Gadd45β and MKK7 UniprotKB accession numbers (ACs). I suggest that you go to [UniprotKB](http://www.uniprot.org) and retrieve them. Remember that we are using the human proteins! If you know well UniprotKB or you are too lazy, here they are:

Gadd45β UniprotKB AC: O75293 
MKK7 UniprotKB AC: O14733 

```

###1. Build the homology model of Gadd45β
At the time of writing, the crystal structure of Gadd45β is not available in the PDB. If it has become available in the meanwhile, we will pretend it is not available: it does not make any difference to our purposes.  We want therefore to **build a structural model** using the homology modelling technique. We will do it using HHPred (http://toolkit.tuebingen.mpg.de/hhpred), an online resource for homology modelling and more. This task is described step by step in the [tutorial on homology modelling](tutorial_on_homology_modelling.md). If you are already familiar with homology modelling, you can download the model provided in the [pdb](data/pdb) folder and go to the next step.

###2. Retrieve the crystal structure of the most appropriate conformation for MKK7
The crystal structure of MKK7 is available in the **Protein Data Bank (PDB)** and we need to identify the PDB code of the most suitable conformation.

This can be done a) by directly going to the PDB or b) passing through the UniProt.

a) By directly going to the [PDB](http://www.rcsb.org/pdb/home/home.do)

Click on "Advanced search".
In the "Choose a Query Type" drop down menu choose "UniProtKB Accession Number(s)" and paste the MKK7 UniProt AC (**O14733**) in the text box.
Click on "Result Count". How many structures are available for MKK7? 
Click on "Submit Query" and inspect the structures available. Which one seems the most appropriate for our purposes?

b) By passing through the UniProt
Go to UniProt (http://www.uniprot.org), type the MKK7 UniProt AC (O14733) in the text box at the top and click on Search.
On the result page, go to the structural information (you can scroll-down until you reach the Structure section or directly click on the "Structure" link on the left). 
Select the RCSB PDB link destination. The structures available in the PDB for MKK7 will appear in the "Entry" column. You will have to inspect each of them (by clicking on their PDB codes) in order to decide which is the most appropriate for our purposes.


###3. Identify appropriate restraints to limit the number of docking conformations
Structural models of complexes are more reliable if you can apply "restraints". Restraints can be of many different types: a known or likely bond between two residues (one belonging to the receptor and the other one to the ligand, actraction/repulsion properties of one or more residues in one structure or both, etc). In many cases, we just know two proteins do interact but we have no idea about possible restraints. However, in some cases they can be extracted from what we know about the interaction mechanism (from the literature or experiments carried out in your lab). 

In this case, we know that *Gadd45β acidic loop 1 interacts with MKK7 Lys149, i.e. with the ATP binding site*. More specifically,(Papa et al, JBC 2007) found that residues within putative Gadd45β acidic loops 1 and 2 – i.e. Glu65, Glu66 and Glu113 – directly contact basic residues within the catalytic pocket of MKK7 – i.e Lys149, Lys157 and Arg162.

MKK7 residue | Gadd45β residue
:---------------------:|:-----------------------:
K149 (ATP binding site)| E65
R162                   | E66
K157                   | E113

In order to use the bonds between these residues as restraints in building the model of the complex, we need to identify them in the MKK7 and Gadd45β protein structures. We will first identify them in the protein sequences and subsequently in the protein structures. Notice that PDB residue numbering may differ from UniProt numbering.

####Identification of K149, R162, and K157 in the protein sequence of MKK7 (MKK UniProt AC: O14733)
a) Go to the "Function" section of the UniProt entry for MKK7. Check whether the ATP binding site residue has the same number as the one reported in the literature (K149);
b) Click on the residue Position(s) and identify the sequence context of K149 (e.g. the three residues before and after: IAVKQMR);
c) Starting from the position of K149 identify K157 and its sequence context (SGNKEEN) and R162 and its sequence context (ENKRILM);
d) Go to the MKK7 PDB entry (http://www.rcsb.org/pdb/explore/explore.do?pdbId=2DYL) and click on the "Sequence" button in the menu bar. Identify the IAVKQMR sequence and the residue number corresponding to K149.
e) With a similar procedure identify the 2DYL residue numbers corresponding to K157 and R162;
This can also be done by inspecting the PDB text file that you can download by selecting the "PDB file" option from the "Display Files" drop-down menu.
You should also verify to which PDB chain this residues belongs. Notice that 2DYL is a single chain structure .

####Identification of E65, E66, and E113 in the protein sequence of Gadd45β (Gadd45β Uniprot AC: O75293)
With a procedure similar to the one adopted for MKK7, go to Uniprot and identify the sequence context of Gadd45β E65, E66, and E113. This will help you to find the corresponding residues in the protein structure (gadd45B_model.pdb). 

For your convenience, you can find below a table summarising this information.

|protein name|sequence residue num |sequence context |structure file   |structure residue num|
|------------|:---------------------:|:-----------------:|:-----------------:|:---------------------:|
|MKK7        |K149		   |IAVKQMR          |2DYL.pdb         |K165                 |
|            |R162                 |ENKRILM          |2DYL.pdb         |R178                 |
|            |K157                 |SGNKEEN          |2DYL.pdb         |K173                 |
|            |                     |                 |                 |                     | 
|Gadd45β     |E65                  |IDEEEEDD	     |gadd45B_model.pdb|E65                  |				
|            |E66		   |IDEEEEDD         |gadd45B_model.pdb|E66                  |
|            |E113                 |QGTTEARD         |gadd45B_model.pdb|E113


###4. Down to business: modelling the Gadd45β-MKK7 complex using ClusPro
Now we are ready to model the structure of the Gadd45β-MKK7 complex. The data we are going to use are:
1. MKK7 PDB code: 2DYL
2. The file containing the homology model for Gadd45β: gadd45B_model.pdb
3. The restraints previously identified 

a) Go to the ClusPro webpage (http://cluspro.bu.edu/home.php). Here, you may want to create an account by clicking "Sign up for an account". You will receive an email with your account details that you can use to sign in.
b) We are not going to create an account. Therefore, click on "Use the server without the benefits of your own account". 
c) In the ClusPro input page that will appear, you have to 
* specify a Job Name  
* insert the MKK7 PDB code (2DYL) in the Receptor text box. Do we also need to specify the chain? Why?
* upload gadd45B_model.pdb for the Ligand. Do we also need to also specify the chain? Why? 
* Then, use the *Advanced Options* to set the restraint. 

By clicking on the Advanced Options, you will notice that several options appears. Spend a few minutes inspecting the other options and try to understand what they do. In particular, what can you do with the "Attraction and Repulsion" and "Restraints" options? How could we use this options in our case?


####Attraction and Repulsion
We want to run a first job (I suggest "mkk7-gadd45b-attr-rep" or something similar for the job name) where we
specify that the MKK7 Lys149 (2DYL: K165), R162 (2DYL: R178) and Lys157 (2DYL: K173) have attractive properties toward Gadd45β Glu65 (gadd45B_model.pdb: E65), Glu66 (gadd45B_model.pdb: E66), and Glu113 (gadd45B_model.pdb: E113), respectively.
This can be done by specifying "a-165 a-178 a-173" in the "Attraction" text box for the Receptor and "a-65 a-66 a-113" in the "Attraction" text box for the Ligand.
You can now run it.
Notice that it may take hours to get your results.

####Restraints
We also want to see how the "Restraints" option works. This is a bit more complicated, but just a little bit. 
If you have any knowledge about residues that should be close together in the interface, you can make a restraints file and use the knowledge you have to only produce results which satisfy your restraints. For example, the literature can provide information about interacting residues.  Restraints can be combined into restraint groups, and groups are combined into a restraint set, which allows users to specify some logic about how many restraints are required to be satisfied.
The restraint file needs to be in *json* format and you can generate it using the *restraint generator*. Each restraint specifies a pair of residues, one from the receptor and one form the ligand, and an acceptable distance range for the restraint to be satisfied. Once you have created a set of restraints, you can copy it to a text file with a .json suffix:
```
{"required":1,"groups":[{"required":2,"restraints":[{"type":"residue","dmax":2.5,"dmin":1,"rec_chain":"A165",
"lig_chain":"A65"}, {"type":"residue","dmax":2.5,"dmin":1,"rec_chain":"A178","lig_chain":"A66"},
{"type":"residue","dmax":4,"dmin":1,"rec_chain":"A173","lig_chain":"A113"}]}]}
```
This is the file you will upload in the ClusPro's Restraints option. Then, you can run your job.

###5. Analysis of ClusPro results
The goal of ClusPro results' analyses is to identify, among the large number of docking conformations, those better fullfilling the restraints you have imposed. First, we have to navigate the ClusPro output page and identify sets of solutions ("models") we will download and further inspect. 
The inspection of the docking models will be carried out using the [UCSF Chimera](https://www.cgl.ucsf.edu/chimera/) program for the interactive visualization and analysis of molecular structures. The docking results' analysis using UCSF Chimera is described in the [tutorial on docking results analysis using UCSF Chimera] (tutorial_on_docking_results_using_chimera.md). If you are familiar with a different molecular graphics program (e.g. PyMol), don't hesitate to use it.
 
In the ClusPro output page you can:

a) Review the details of your Job (what input structures? What options have you used?)

b) View the Model Scores. The most important aspect is to check whether there are docking solutions that form large clusters
- In our case, the mkk7-gadd45b-attr-re Cluster 0 has 134 members, which is a good number; 
- mkk7-gadd45b-restrai Cluster 0 has 132 members;
In principle, you should choose – as your final solution - a conformation belonging to the largest cluster. However, there are other parameters that count. An important one is whether the predicted complex fulfils the input restraints, i.e. (in our case), whether the MKK7 ATP bindig site actually interacts with Gadd45β residues in loop 1. In order to check this, you have to inspect the models displayed in the output page (each model is a representative of a cluster) and download those that seem a potentially correct conformation.
As mentioned above, you can use a molecular graphics software to display each model, highlight MKK7 K149, R162, K157 and verify their position relatively to Gadd45β E65, E66, and E113. 

c) In the output page, you will see four different choices for your docking results, "Balanced", "Electrostatic-favored", and so on. Which one should you choose?
CluPro provides many different options for docking because they believe good results go hand-in-hand with experimental knowledge of the complex. If you don't have any prior knowledge of what forces dominate in your complex, they recommend using the balanced coefficients. 
For example, if you know from experiments that the receptor and the ligand have been observed to separate when subjected to ionic force in vitro, the interaction will likely be "Electrostatic-favored". Instead, if the two partners tend to separate when immersed in apolar solvents, they will likely be "Hydrophobic separated". If your complex is antibody-antigen, they recommend using the antibody mode.

d) In our case, we know that interactions between MKK7 and Gadd45β occur between basic (alkaline) MKK7 residues and acidic Gadd45 residues. Therefore, it makes sense to also have a look at "Electrostatic-favored" solutions. 

###6.References

#####Docking
* Halperin I, Ma B, Wolfson H, Nussinov R (2002) Principles of docking: an overview of search algorithms and a guide to scoring functions. PROTEINS: Structure, Function, and Generics 47: 409-443
* Katchalski-Katzir,E., Shariv,I., Eisenstein,M., Friesem,A., Aflalo,C. and Vakser,I.A. (1992) Molecular surface recognition—determination of geometric fit between proteins and their ligands by correlation techniques. Proc. Natl Acad. Sci. USA, 89, 2195–2199.
* Vakser,I.A. (1996) Low-resolution docking: prediction of complexes for underdetermined structures. Biopolymers, 39, 455–464.
* Ritchie,D.W. and Kemp,G.J.L. (2000) Protein docking using spherical polar Fourier correlations. Proteins, 39, 178–194.

#####Clustering
* Shortle,D., Simons,K.T. and Baker,D. (1998) Clustering of low-energy conformations near the native structures of small proteins. Proc. Natl Acad. Sci., USA, 95, 11158–11162
* Camacho,C.J. and Gatchell,D. (2003) Successful discrimination of protein interactions. Proteins, 52, 92–97

#####ClusPro
* Comeau, S. R., D. Gatchell, S. Vajda, and C. J. Camacho. 2004. ClusPro: an automated docking and discrimination method for the prediction of protein complexes. Bioinformatics. 20:45–50

Haddock 
* Dominguez C, Boelens R, Bonvin AMJJ (2003) HADDOCK:  A Protein−Protein Docking Approach Based on Biochemical or Biophysical Information. JACS 125, 1731
* de Vries SJ, van Dijk M, Bonvin AMJJ (2010) The HADDOCK web server for data-driven biomolecular docking. Nature Protocols, 5, 883-897 

#####Others
* Papa S, Monti SM, Vitale RM, Bubici C, Jayawardena S, Alvarez K, De Smaele E, Dathan N, Pedone C, Menotti Ruvo, Franzoso G (2007) Insights into the Structural Basis of the GADD45_-mediated Inactivation of the JNK Kinase, MKK7/JNKK2. JBC 282:19029-19041
* Tornatore L, Marasco D, Dathan N, Vitale RM, Benedetti E, Papa S, Franzoso G, Ruvo M, Monti SM (2008) J. Mol. Biol. 378: 97–111
* Perkins JR, Diboun I, Dessailly BH, Lees JG, Orengo C (2010) Transient Protein-Protein Interactions: Structural, Functional, and Network Properties. Structure 18:1233-1243
