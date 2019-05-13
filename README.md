# How Bacterial Diversity Impacts the Hatching Success of European Birds

### GRAD BMIG 6202 001 Fundamentals of the Human Microbiome Spring 2019

## Hypothesis

Bacterial diversity will have a noticeable relationship with hatching success.

Certain bacterial taxa will have higher appearance rates in clutches with lower success rates.

## Introduction

16S rRNA Sequence data was obtained from the ENA from the paper [“Bacterial density rather than diversity correlates with hatching success across different avian species”](https://academic.oup.com/femsec/article/94/3/fiy022/4847879).

The authors monitored 600 nest boxes and several wild nests and swabbed the eggs at the start of incubation and after the clutch was completed. Any data from nests where no eggs hatched was thrown out in case of parental abandonment.

The final dataset included 157 clutches from 17 bird species.

 ## Methods
 
##### Imported into QIIME2
Sequence data was first obtained from [Qiita](https://qiita.ucsd.edu/study/description/1632#). A subset of the data was run through several steps of the process to help formalize the planned pipeline. In this process I gained a better understanding of Qiime2 and its data types. The Qiita repository included an extremely useful graphic that helped show the pipeline the authors ran through and highlighted many of their parameters that would be used. When looking at Qiita data I ran into several issues because the data was not demultplexed, but many attempts to demultiplex according to the papers instructions and the moving picture tutorial guidelines failed. In the final process data that was already demultiplexed was used. 

After the trial run had worked out the kinks in the planned pipeline, demultiplexed sequence data was downloaded from the [Eureopean Nucleotide Archive](https://www.ebi.ac.uk/ena/data/view/PRJEB14786) onto the UAMS HPC. Data was then imported into Qiime2 v2019.1. 

##### Deblur Trim Length 100
After data was imported the Deblur tool was used for quality filtering. The trim length was chosen by what the authors has specified in the Qiita pipeline as 100. 

##### Closed Reference OTU picking (Greengenes)
Next Closed Reference OTU picking was preformed with greengenes. This was based off data in the project page on Qiita. The paper actually claimed they used Open Reference OTU picking with greengenes v10_13. However Qiita specifically listed closed reference.I downloaded the greengenes fileset from and imported the files in to QIIME2 and then these files were used for Closed Reference Picking.

At this point data was transferred to another machine, running QIIME2 v2018.11.

#### Filtered mitochondria, archaea, and low frequency OTUs
Next the Archea, Chloroplasts, Mitochondria, and low frequency OTUs were removed. QIIME included a way to remove specfic taxa with just the parameters of archea, chloroplasts, and mitochondria, however for OTU frequency a parameter needed to be chosen. The paper specified the frequency they removed was .005% and under of total OTU frequency. To calculate this for my remaining dataset I looked at the visualization of the data to get the total frequency and multiplied by .00005 for the frequency to drop. 

##### Align to tree  Core Metrics     Taxa Barplot
Before filtering there were 3,000 OTUs. After final filtering was complete I had ~800 OTUs remaining, compared to the original authors ~500 OTUs. It was a larger gap than I had hoped for, but not unuseable. For final analyze I aligned the data to a tree, created PCoA plots with the core metrics command, and created a taxonomic barchart. 

##### Beta Diversity 
A  box and whisker visualization of hatching success was created based on Unweighted Unifrac data form the core metric output.

## Results Text
The ratios of common bacterial taxa are similar between species regardless of their hatching success rates.

## Discussion

* Research with negative results or small effect sizes can still contribute to the field. 
* Reproducibility should always be a major focus in scientific papers. 

The results here are of a small effect size, in fact even though the original paper outlines the sequencing methods in detail, it focuses more heavily on the results of the culturing methods. However, in science even negative results deserve to be considered, as focusing only on the positive is harmul for the scientific community. It removes the search for truth and knowledge instead searching for popularity and publishing power. Even though the effect and results are small, the detailing of sequencing metholodgy shows great value and encourages reproduction. Therefore in this study I have worked to ensure my methods are well described, since a focus on reproduction allows a paper to benefit all of science and health, not just a particular niche or subfield. 

## Results Images

* Unweighted Unifrac by Hatching Success
![alt text](/hpc/images/UU/UnWeightedUFHatchingSuccess.png "UnWeighted Unifrac by Hatching Success")

* Weighted Unifrac by Hatching Success
![alt text](/hpc/images/WU/WeightedUniFracHatchingSuccess_withNulls_remove.png "Weighted Unifrac by Hatching Success")

* Beta Diversity Unweighted Unifrac Hatching Success
![alt text](/hpc/images/boxwhisker.png "Weighted Unifrac by Hatching Success")

[SVG of bacterial diversity by host bird species](https://github.com/sutecht-uams/HowBacterialDiversityImpactstheHatchingSuccessofEuropeanBirds/blob/master/hpc/images/level-2-bars(2).svg)

The above SVG was broken down by species in Inkspace, and hatching succes numbers were provided by the original paper.
* Bacteria Species
![alt text](/hpc/images/level-2-legend(2).png "Bacteria Species")
* Athene_noctua 100.0% Hatching Success
![alt text](/hpc/images/Athene_noctua_100_0.png "Athene_noctua 100.0% Hatching Success")
* Falco tinnunculus 100.0% Hatching Success
![alt text](/hpc/images/Falco_tinnunculus_100_0.png "Falco tinnunculus 100.0% Hatching Success")
* Columbia livia 99.2% Hatching Success
![alt text](/hpc/images/Columbia_livia_99_2.png "Columbia livia 99.2% Hatching Success")
* Otus scops 98.6% Hatching Success
![alt text](/hpc/images/Otus_scops_98_6.png "Otus scops 98.6% Hatching Success")
* Coracias garrulus 97.5% Hatching Success
![alt text](/hpc/images/Coracias_garrulus_97_5.png "Coracias garrulus 97.5% Hatching Success")
* Parus major 96.4% Hatching Success
![alt text](/hpc/images/Parus_major_96_4.png "Parus major 96.4% Hatching Success")
* Serinus serinus 95.7% Hatching Success
![alt text](/hpc/images/Serinus_serinus_95.7.png "Serinus serinus 95.7% Hatching Success")
* Passer montanus 95.2% Hatching Success
![alt text](/hpc/images/Passer_montanus_95_2.png "Passer montanus 95.2% Hatching Success")
* Hirundo rustica 95.0% Hatching Success
![alt text](/hpc/images/Hirundo_rustica_95_0.png "Hirundo rustica 95.0% Hatching Success")
* Corvusmonedula 94.8% Hatching Success
![alt text](/hpc/images/Corvus_monedula_94_8.png "Corvusmonedula 94.8% Hatching Success")
* Oenathe_leucura 93.7% Hatching Success
![alt text](/hpc/images/Oenathe_leucura_93_7.png "Oenathe_leucura 93.7% Hatching Success")
* Pica pica 92.0% Hatching Success
![alt text](/hpc/images/Pica_pica_92_0.png "Pica pica 92.0% Hatching Success")
* Sturnus unicolor 91.3% Hatching Success
![alt text](/hpc/images/Sturnus_unicolor_91_3.png "Sturnus unicolor 91.3% Hatching Success")
* Lanius meridionalis 91.2% Hatching Success
![alt text](/hpc/images/Lanius_meridionalis_91_2.png "Lanius meridionalis 91.2% Hatching Success")
* Pyrrhocorax pyrrhocorax 90.4% Hatching Success
![alt text](/hpc/images/Pyrrhocorax_pyrrhocorax_90_4.png "Pyrrhocorax pyrrhocorax 90.4% Hatching Success")
* Turdus merula 89.2% Hatching Success
![alt text](/hpc/images/Turdus_merula_89_2.png "Turdus merula 89.2% Hatching Success")
* Upupa epops 82.3% Hatching Success
![alt text](/hpc/images/Upupa_epops_82_3.png "Upupa epops 82.3% Hatching Success")

* Unweighted Unifrac by Spieces
 ![alt text](/hpc/images/UU/UnWeightedSpeices.png "UnWeighted Unifrac by Spieces")

<img src="/hpc/images/UU/list1.png" height="400"><img src="/hpc/images/UU/list2.png" height="300">

* Weighted Unifrac by Spieces
 ![alt text](/hpc/images/WU/WeightedUniFracSpecies.png "Weighted Unifrac by Spieces")

<img src="/hpc/images/WU/speiceslabelWU1.png" height="400"><img src="/hpc/images/WU/specieslabelWU2.png" height="300">

Tree before Archea/Mitochondria/Chloroplasts are removed
[Tree at ITOL](https://itol.embl.de/tree/991976123347171557017399) 
![alt text](/hpc/images/P5-B6R1OKpvN-o3fvtUm1A.png "Tree")

Tree after Archea/Mitochondria/Chloroplasts are removed
[Tree at ITOL](https://itol.embl.de/tree/1443035150384711557020271) 
![alt text](/hpc/images/pid-zieN1CQ3V--4RsaC9w.png "Tree")

### References (WIP)

* Juan Manuel Peralta-Sánchez Antonio Manuel Martín-Platero Laura Wegener-Parfrey Manuel Martínez-Bueno Sonia Rodríguez-Ruano José Antonio Navas-Molina Yoshiki Vázquez-Baeza David Martín-Gálvez Manuel Martín-Vivaldi Juan Diego Ibáñez-Álamo Rob Knight Juan José Soler   FEMS Microbiology Ecology, Volume 94, Issue 3, March 2018, fiy022, https://doi.org/10.1093/femsec/fiy022 [link](https://academic.oup.com/femsec/article/94/3/fiy022/4847879)

* QIIME2 https://peerj.com/preprints/27295/ 

* Catherine Lozupone, Rob Knight UniFrac: a New Phylogenetic Method for Comparing Microbial Communities https://aem.asm.org/content/71/12/8228

*	Tree Of Life v1.0 (Ciccarelli FD, et al., Science.; 2006 Mar 3. 311(5765): 1283-7)

* ENA https://www.ebi.ac.uk/ena/data/view/PRJEB14786 ERP016455



