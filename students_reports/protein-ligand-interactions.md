##Features of protein-ligand interactions identified in group work

######International master in Bioinformatics, Bologna, AA 2015/2016


**Protein-Protein Interactions**

general structure:
1 we havea core region with higher hydrophobicity with tightly packed residues with high hydrophobicity.
We have edged or rim regions.
In lateral region there are more polar res and a polar behaviour and also water binded.
Not easy to find the border.
PPI have a low number of hotspots.
Geometry is quite important because generally are more often flat or convex.
And the res occurrence is quite similar of the core of the protein.
The factor that regulates: concentration of the protein, protein affinity, presence of other protein. Electric field around protein. PTM, structural domains involved.
Examples:

actine-myosine interactions in muscle contractions
p53
cytocrome
Antibody/antibody sometimes is PPI or other kind of molecules.


If you have to design an algorithm to predict PPI?
Find hydrophobic spots in structure.
Looking for residues on the surface. And look for neighbors res. 
Using HMM we can build a model considering the rims and the core.
Graph could help identify clusters.


**Protein small-ligands interations**

small-deeper pockets
inhibitors or cofactors
can be formed both stable and transient intercations.
Ligands can be elements, ions or small molecules in general.
Small means not protein,not DNA/RNA not macromolecules.
Examples: 
cytochrome c stable linked with – heme group in cellular respiration ( same as the one found in hemoglobin with a different function)
penicillin binds irreversibly D-D-transpeptidase and prevents bacterial wall to maintain itself

If you have to design an algorithm to predict Protein small ligand?
Given the structure of protein or ligand we can find the match with the lowest energy so we can assume that can be a docking possibility.

Stable interactions

They are permanent interactions and last longer. 
Usually these proteins are co-expressed and co-localized in high concentration.
Proteins of this j=kind need to be expressed at the same time and in the same place.

Example:
ATPase in which more subunits interact to produce ATP and interact in stable ways.
In general any complex has a stable interaction with sub-units.


transient interactions

investigating transient interactions, first of all as the name sad there are not permanent (exact time unknown)
divide between :
weak (last less time; seconds or less)
smaller interface (about 12 residues from a couple of example)
lower affinity (related to number of bonds)
strong (last longer; seconds or more)
higher affinity

very low kb at level of micro molars for weak interaction and strong interaction are in the range of millimolars.

example of cascade signal (from outside to inside the cell) that must be quick.

Example :
Laccase (fungal) where we have Glycosilation site and short pattern (N X S/T N)
TP53 has got NLS (nuclear localisation signal, 12 res) and NES (17 res, Nuclear export signal)



