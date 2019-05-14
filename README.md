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

#### Annotated Bibliography
1.  Peralta-Sánchez et al. “Bacterial density rather than diversity correlates with hatching success across different avian species” FEMS Microbiology Ecology, 2018, Vol. 94, Issue 3.

The authors investigated whether bacterial density and bacterial assembly influenced the hatching success of wild birds in the Hoya de Guadix plateau of Spain.  Nests were visited daily and swabs were gathered at the beginning of incubation and after hatching was complete. The length and width off each egg was measured with a caliper after swabbing. The collected swabs were used for culturing in agar plates which were used to estimate the bacterial density. Fingerprinting was performed with ARISA and 16s rRNA sequencing was performed with HiSeq Illumina which were used to study bacterial community assembly. They found from the culturing that density was negatively correlated with hatching success. However, the sequencing data did not show a strong correlation with hatching success. They noted some differences in the Unweighted and Weighted UniFrac data they they theorized could potentially mean that rare taxa had a small effect.


2. Leinonen, Rasko et al. “The European Nucleotide Archive” Nucleic Acids Research, 2011, Vol. 39, Database issue, D28–D31

The European Nucleotide Archive is a publicly available database of nucleotide sequences and part of the International Nucleotide Sequence Database Collaboration along with GenBank and the DNA Databank of Japan. It contains the Sequence Read Archive, the Trace Archive, and the EMBL-Bank. The EMBL-Bank and SRA both allow the public to submit data, and many improvements to how data can be submitted are covered in this paper. Data can be downloaded in several formats including xml and fastq files. Data can be searched and even downloaded in bulk with FTP. This is a very useful tool and it is fantastic that the researchers and employees at the European Bioinformatics Institute made this archive a reality.

3. Collins, Francis and Tabak, Lawrence. NIH plans to enhance reproducibility. Nature, 2014, vol. 505, pp. 612-613.    

Scientific research, and biomedical research especially, are going through a crises and more and more published papers are impossible to reproduce. The NIH believes this is not due to any purposeful misconduct but due to a variety of problems in the community such as tenure rewards, focus on high impact journals, hiding information from competition, poor study design, and more. Since reproducibility is such a core part of science, the community must improve. NIH lays out its current plans for improvement in this paper. Improvements to mandatory training, new reviewer checklists, and a dedicated "scientific premise" reviewer are currently being piloted. NIH is also working to setup a data repository where data can be shared even if it is not associated with a published paper. NIH also encourages journals to be more open to negative data and correction papers.

4. Ravel, Jacques and Wommack, K Eric. All hail reproducibility in microbiome research. Microbiome, 2014, 2:8  

The Editor in Chief and another editor of the journal Microbiome present their stance on reproducibility of research. They believe that the journals themselves are the key to ensuring published papers have data sets available. They provide a detailed list of useful tools and sites that researches can use including SRA, dbGAP, FigShare, Github, and iPython Notebooks, as well recommending a previous paper as an example of correct datasharing. While the named tools are well explained, it might have been more helpful if the authors had included them in a table or sidebar. With this method researchers looking for new tools could quickly reference the list, and more options could be included without bogging down the narrative. The paper ends with the declaration that Microbiome intends to ask authors to provide accessible data, but does not detail if this will be an actual requirement or simply an option that researches can easily decline.

5. Gonzalez, Antonio et al. “Qiita: rapid, web-enabled microbiome meta-analysis” Nature Methods, 2018, Vol. 15, pp 796-798

Qiita is a web based platform that not only stores sequence data, but stores it in the rawest form possible along with all the steps and parameters used to get from raw data to final analysis. The goal of the platform is to allow users that are not bioinformaticians to perform metanalyses on data using pipelines like QIIME2. Qiita automatically deposits data to the ENA as well. By accepting only the rawest form of data, Qiita is ensuring the data can be reused with new analytic technologies as they are created. Studies with high quality metadata are labeled as Gold studies, in order to encourage users to aim for high quality in their work as well. The lead author on the work is a programmer, so we can have confidence the backend technology is sound and well supported. Qiita is a very useful platform for new researchers and veterans alike.

6. Boylen, Evan et al. “QIIME 2: Reproducible, interactive, scalable, and extensible microbiome data science” PeerJ Preprints 6:e27295v2 

QIIME 2 is the successor to QIIME, moving the microbial analytic pipeline platform forward and allowing new technology and opportunity. To allow for growth in technologies, QIIME2 is based around plugins. Various implementations of denoising, taxanomic alignment, and more are available as plugins and can be updated or replaced easily as new algorithms are developed. In addition, QIIME2 provides interactive visualizations with provenance tracking. QIIME2 also works to be accessible to users from various backgrounds and is free and open source. Its design aimed for the future, long list of high profile authors, and most importantly the success of its predecessor QIMME gives confidence that QIIME2 will be a fantastic resource for the field.


7. Caporaso, Gregory et al. “QIIME allows analysis of high-throughput community sequencing data” Nature Methods, 2010, Vol. 7, Issue 5. Pp335-336

QIIME, quantitative insights into microbial ecology, is a tool that allows users to work through an entire analysis pipeline. As new sequencing technology increases the size of datasets, the authors found they could not find tools that offered a library for demultiplexing, a library for taxonomy assignment, and a set of analytic tools for continuing with the data. Using PyCogent they created the QIIME platform. It is built to be modular so that functions can be added over time. They then tested the tool on a new twin study to verify it. Written by a group of experts in the field, we know QIIME was a useful tool until its successor QIIME2 was created. 

8. Amir, Amnon et al. “Deblur Rapidly Resolves Single-Nucleotide Community Sequence Patterns” mSystems,2017, Vol. 2, Issue 2, e00191-16;

DeBlur is a tool for denoising datasets, or removing error sequences. To do this it uses a sub-Operational-Taxanomic-Unit approach, similar to other popular algorithms DADA2 and UNOISE2. Unlike those tools DeBlur can be more easily parallelized because it operates on every sample independently. The algorithm first sorts the sequences by abundance, then subtracts the predicted error number from neighbors based on Hamming distance. If a sequence’s abundance drops to 0, it is removed as likely an error.  

9. Callahan, Benjamin et al. “DADA2: High-resolution sample inference from Illumina amplicon data” Nature Methods, 2016, Vol. 13, pp 581-583

A successor to DADA, Divisive Amplicon  Denoising Algorithm, DADA2 is a tool for correcting errors in Illimuna amplicon data. Many researchers are handling the issues of amplicon errors with OTU clustering, however; the authors feel important real variations may be getting lost. DADA2 was tested against several similar methods such as Mothur, and the authors found that it the most accurate. 


10.  DeSantis, et al. “Greengenes, a Chimera-Checked 16S rRNA Gene Database and Workbench Compatible with ARB” Applied and Environmental Microbiology. Jul 2006, Vol. 72, Issue 7, pp 5069-5072

At the time of the paper there was a major issue with public sequence databases having a large number of chimeric sequences. When using PCR methods the sequence fragments must be aligned and rejoined to make longer sequences, but if done improperly a sequence made from unrelated contigs can be created, a chimera. Once the chimera is out there, others may try to align data to the sequence of this nonexistent creature. To resolve this issue, the authors have created a new database that checks data for chimeras, while also providing standard alignment, and taxonomic classification. The chimera checking algorithm is based on Bellerophon, but with modifications that make it significantly faster to run and provide a divergence ratio. DeSantis and Hugenholtz have worked on many tools in the field. DeSantic worked on NAST and PyNAST and has six publications with more than 1000 citations. Hugenholtz worked on the original Bellerophon that was adapted as part of this project as well as CheckM, NAST, and CRISPR. He has a dozen publications with over 1000 citations each. Clearly these authors are good tool makers in the field.

11. Rideout, Jai Ram et al. “Subsampled open-reference clustering creates consistent, comprehensive OUT definitions and scales to billions of sequences” PeerJ. 2014, eCollection e545

Several familiar names from the field including Rideout, Knight, and Caporaso contributed to
this paper on a technique for OTU clustering. Closed reference OTU clustering is fast and aligns
sequences to a reference database. However, any novel sequences that do not align are thrown away. The alternative is De Novo clustering, which clusters sequences by comparing them to each other instead of references. But this method is very slow because the comparisons can not be easily done in parallel, so it is not reasonable to use this on large data sets. One strategy to get the best of both options is open-reference picking, where first Closed Reference OTU picking is done, and the novel sequences that remain are then de novo clustered. However, in sets with a large number of novel sequences this can still be too slow. The authors have suggested a new strategy to speed this up. After the initial closed reference run, a subsample of the remaining sequences is de novo clustered. Then the remaining sequences are close reference clustered using the new OTUs from the subsample. This can be repeated
as necessary, allowing for the benefits of open reference OTU picking with faster results. The authors ran several comparison test and found their results align well with existing methods, with improved runtimes in datasets with many novel OTUs. Since these authors are some of the common writers in the field we have good reason to trust their results.

12. Lozupone, Catherine et al. UniFrac: A Phylogenetic Method for Comparing Microbial Communities. Applied and Environmental Microbiology, Dec 2005, Vol. 71, Issue 12, pp. 8228-8235

This work introduces a new tool and metric for measuring and comparing diversity in microbial communities called UniFrac. The metric, called unique fraction metric, measures phylogenetic distance.  This will better determine if environments are similar or distinct than just comparing the OTUs alone, as different OTUs will still share many branches in similar communities but have more evolutionary diversity in others. To display their new tool and metric, a comparison was made between cultured and uncultured samples of sea water, sea ice, and sediment. Using UniFrac they determined that where different OTUs live was less effected by geography than by the environment type. This could not have been determined without a measurement made for comparing large numbers of sequences from extremely different geographic locations and environments, perfectly demonstrating an example use case for their new tool.  Knight was a professor at University of Colorado at Boulder when Lozupone was a pre-doctoral student. She has since continued to work in the field and now has her own faculty position1.

13. Lozupone, Catherine et al. Quantitative and Qualitative β Diversity Measure Lead to Different Insights into Factors That Structure Microbial Communities. Applied and Environmental Microbiology, Feb 2007, Vol. 73, Issue 5, pp 1576-1585

The creators of UniFrac return along with other researchers to introduce a new metric added to the UniFrac tool. The added metric, weighted UniFrac, modifies the original unweighted UniFrac to factor in quantitative measures of β diversity, while leaving the original metric available to measure qualitative diversity. The authors reproduced existing studies to demonstrate both the validity of the new weighted UniFrac measure and possible use cases for both weighted and unweighted UniFrac metrics. The first study reproduced was of geothermal vents from Yellowstone with data from a 2007 paper by Mathur et al. Weighted UniFrac agreed with the original paper’s quantitative metric that the temperature was not as important of a factor for diversity as the minerals available. The unweighted version, measuring only the phylogenetic difference in OTUs without considering their frequency, favored temperature as the more important factor. The second study reproduced shows another case where unweighted and weighted UniFrac show unique insights; examining the composition of microbiota in the guts of healthy and overweight mice with data from Ley et al (2005). Weighted UniFrac clustered the sequences by the mice obesity phenotypes, however unweighted UniFrac clustered them by their hereditary relationships. Quantitative and qualitative measures are both useful and having both makes UniFrac an even more powerful tool. 

14. Rognes, Torbjorn et al. “VSEARCH: a versatile open source tool for metagenomics” PeerJ, 2016, 4:e2584 eCollection 2016.

VSEARCH was created as an alternative to USEARCH. USEARCH was a useful and popular tool but was closed source and was not entirely free to use. VSEARCH allows users to detect chimeras, search, cluster by similarity, dereplicate, and more. It is free and open source, making it a superior tool for academics and anyone interested in more open science and software. 
15. Price, Morgan et al. “FastTree 2 – Approximately Maximum-Likelihood Trees for Large Alignments”

FastTree 1 was a scalable way to quickly make phylogenic trees. It was a minimum evolution method, which is very fast, but not as accurate as maximum likelihood methods. FastTree 2 first uses a minimum evolution algorithm, then uses maximum likelihood nearest neighbor interchanges to improve the tree. FastTree 2 is an “an approximately-maximum-likelihood method.” It is sill less accurate than true maximum likelihood approaches, but remains accurate enough for many uses with impressive speed that can be used on large datasets. 

16. Katoh, Kazutaka and Standley, Daron. “ArticleFast TrackMAFFT Multiple Sequence Alignment Software Version 7: Improvements in Performance and Usability” Molecular Biology and Evolution, 2013, Vol 30, Issue 4, pp 772-780

The original MAFFT program from 2002 is a multiple sequence alignment tool. Version 7 is a large enough update to warrant a new paper. New features have been added such as the ability to add unaligned sequences to an existing alignment. Each new feature is described here with examples. It is great to see authors continuing to support and improve their work so many years later. 

17. Bokulich, Nikolas et al. “Quality-filtering vastly improves diversity estimates from Illumina amplicon sequencing” Nature Methods, 2012, Vol. 10, Issue 1, pp 57-59

The authors created a strategy for improving the quality of Illumina amplicon data. As sequencing becomes faster, easier, and cheaper more data is being produced, and more data with errors is being produced. These paper outlines the tests used to produce the quality guidelines used by the Earth Microbiome Project. 


Annotation references and additional data type references

•	Google Scholar https://scholar.google.com/
•	Editorial Board. Microbiome. https://microbiomejournal.biomedcentral.com/about/editorial-board
•	Antonio González Peña. About my research. https://sites.google.com/site/antgonza/
•	Catherine Lozupone PhD “School of Medicine Biomedical Informatics and Personalized Medicine” University of Colorado Anshutz Campus http://www.ucdenver.edu/academics/colleges/medicalschool/departments/medicine/BIPM/Faculty/Pages/Catherine-Lozupone,-PhD.aspx
•	McDonald, Daniel et al. “The Biological Observation Matrix (BIOM) format or: how I learned to stop worrying and love the ome-ome.” Gigascience. 2012, Vol 1, Issue 1, p 7
•	McKinney, Wes. “Data Structures for Statistical Computing in Python” PROC. OF THE 9th PYTHON IN SCIENCE CONF, 2010
•	Chang, Qin et al. “Variance adjusted weighted UniFrac: a powerful beta diversity measure for comparing communities based on phylogeny” BMC Bioinformatics, 2011, Vol. 12, pp118
•	Chen, Jun et al. “Associating microbiome composition with environmental covariates using generalized UniFrac distances” Bioinformatics, 2012, Vol. 28 Issue 16, pp 2106–2113.
•	McDonald, Daniel et al. “Striped UniFrac: enabling microbiome analysis at unprecedented scale” Nature Methods, 2018, Volume 15, pp 847–848 
•	Weiss, Sophie “Normalization and microbial differential abundance strategies depend upon data characteristics” Microbiome, 2017, Vol. 5, Issue 27
•	Lane, DJ. “Nucleic Acid Techniques in Bacterial Systematics 16S/23S sequencing”, 1991 pp115-175
