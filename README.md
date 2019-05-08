# How Bacterial Diversity Impacts the Hatching Success of European Birds

### GRAD BMIG 6202 001 Fundamentals of the Human Microbiome Spring 2019

## Hypothesis

Bacterial diversity will have a noticeable relationship with hatching success.

Certain bacterial taxa will have higher appearance rates in clutches with lower success rates.

## Introduction

16S rRNA Sequence data was obtained from the EBI from the paper [“Bacterial density rather than diversity correlates with hatching success across different avian species”](https://qiita.ucsd.edu/study/description/1632#).

The authors monitored 600 nest boxes and several wild nests and swabbed the eggs at the start of incubation and after the clutch was completed. Any data from nests where no eggs hatched was thrown out in case of parental abandonment.

The final dataset included 157 clutches from 17 bird species.

 ## Methods
 
##### Imported into QIIME2
Sequence data was first obtained from [Qiita](https://qiita.ucsd.edu/study/description/1632#). A subset of the data was run through several steps of the process to help formalize the planned pipeline. In this process I gained a better understanding of Qiime2 and its data types. The Qiita repository included an extremely useful graphic that helped show the pipeline the authors ran through and highlighted many of their parameters that would be used. When looking at Qiita data I ran into several issues because the data was not demultplexed, but many attempts to demultiplex according to the papers instructions and the moving picture tutorial guidelines failed. In the final process data that was already demultiplexed was used. 

After the trial run had worked out the kinks in the planned pipeline, demultiplexed sequence data was downloaded from the [Eureopean Nucleotide Archive](https://www.ebi.ac.uk/ena/data/view/PRJEB14786) onto the UAMS HPC. Data was then imported into Qiime2 2019. The original study used Qiime v1.9, so this is this first step makes this a reproduction of methods rather than a pure replication.

##### Deblur Trim Length 100
After data was imported the Deblur tool was used for quality filtering. The trim length was chosen by what the authors has specified in the Qiita pipeline as 100. For easier reproduction this should have also been listed in the paper, but was not. 

##### Closed Reference OTU picking (Greengenes)
Next Closed Reference OTU picking was preformed with greengenes. This was based off data in the project page on Qiita. The paper actually claimed they used Open Reference OTU picking with greengenes v10_13. However Qiita specifically listed closed reference.I downloaded the greengenes fileset from and imported the files in to QIIME2 and then these files were used for Closed Reference Picking.

#### Filtered mitochondria, archaea, and low frequency OTUs
Next the Archea, Chloroplasts, Mitochondria, and low frequency OTUs were removed. QIIME included a way to remove specfic taxa with just the parameters of archea, chloroplasts, and mitochondria, however for OTU frequency a parameter needed to be chosen. The paper specified the frequency they removed was .005% and under of total OTU frequency. To calculate this for my remaining dataset I looked at the visualization of the data to get the total frequency and multiplied by .00005 for the frequency to drop. 

##### Align to tree  Core Metrics     Taxa Barplot
Before filtering there were 3,000 OTUs. After final filtering was complete I had ~800 OTUs remaining, compared to the original authors ~500 OTUs. It was a larger gap than I had hoped for, but not unuseable. For final analyze I aligned the data to a tree, created PCoA plots with the core metrics command, and created a taxonomic barchart. 

## Results
The ratios of common bacterial taxa are similar between species regardless of their hatching success rates. Bacterial diversity only has an effect on hatching success if rare taxa are taken into account.

[SVG of bacterial diversity by host bird species](https://github.com/sutecht-uams/HowBacterialDiversityImpactstheHatchingSuccessofEuropeanBirds/blob/master/hpc/images/level-2-bars(2).svg)

## Discussion

Research with negative results or small effect sizes can still contribute to the field. 
Reproducibility should always be a major focus in scientific papers. 

The results here are of a small effect size, in fact even though the original paper outlines the sequencing methods in detail, it focuses more heavily on the results of the culturing methods. However, in science even negative results deserve to be considered, as focusing only on the positive is harmul for the scientific community. It removes the search for truth and knowledge instead searching for popularity and money. Even though the effect and results are small, the detailing of sequencing metholodgy shows great value and encourages reproduction. Therefore in this study I have worked to ensure my methods are well described, since a focus on reproduction allows a paper to benefit all of science and health, not just a particular niche or subfield. 

