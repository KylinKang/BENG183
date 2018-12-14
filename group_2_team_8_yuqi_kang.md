# Handout -- ChIP Sequencing
1. [Introduction](#231)<br>
    1.1 [Advantage of ChIP Sequencing](#2311)<br>
2. [Background Knowledge](#232)<br>
    2.1. [Transcription Factor](#2321)<br>
    2.2. [Gene Regulation and Annotation](#2322)
3. [Workflow](#233)<br>
    3.1. [Library Preparation](#2331)<br>
    3.2. [Sequencing Output Preprocessing](#2332)<br>
    3.3. [Data Analysis](#2333)<br>
4. [Data Visualization](#234)
5. [Important Application](#235)



## 1. Introduction<a name="231"></a>

As a powerful tool of analyzing protein-DNA interaction, ChIP-sequencing combines chromatin immunoprecipitation (ChIP) with next generation sequencing (NGS). It is widely applied in fields of identifying DNA sequence that are bounded by transcription factors, histone modification proteins or RNA polymerase in vivo <a href="https://www.ncbi.nlm.nih.gov/pubmed/17558387">[1]</a>.

It could also be used to examine the function of non-coding regions such as enhancers, silencers and insulators through the genome. When comparing across different samples, it is able to reveal the gene regulation events that play a role in biological pathways and even certain diseases, for example, cancer. 

To capture the DNA-protein interaction, the major steps are as following <a href="https://docs.google.com/presentation/d/1Va34FmS3-DqZXPqmbybBgL1qgNaUwcGcm86wXHkKrlI/edit#slide=id.p2">[2]</a>:
- **Crosslink** crosslink protein and sheer DNA
- **Select** add protein specific antibody 
- **Immunoprecipitate** immunoprecipitate and purify complexes
- **Reverse-Crosslink** reverse crosslinks, purify DNA and preparing for sequencing
- **Sequencing and Align** preprocessing the sequencing output and map the reads to genome
- **Data Analysis and Visualization** apply further analysis on the aligned reads

#### 1) Advantage of ChIP Sequencing<a name="2311"></a>

ChIP-Seq identifies the binding sites of DNA-associated proteins and can be used to map global binding sites for a given protein. Unlike arrays and other approaches used to investigate the epigenome, which are inherently biased because they require probes derived from known sequences, ChIP-Seq does not require prior knowledge. ChIP-Seq delivers genome-wide profiling with massively parallel sequencing, generating millions of counts across multiple samples for cost-effective, precise analysis. Besides this unbiased investigation of epigenetic patterns, ChIP sequencing also have the following advantages compared to other transcription factor binding site detecting methods. <a href="https://www.illumina.com/techniques/sequencing/dna-sequencing/chip-seq.html">[4]</a>

- Captures DNA targets for transcription factors or histone modifications across the entire genome of any organism [4]
- Defines transcription factor binding sites
- Reveals gene regulatory networks in combination with RNA sequencing and methylation analysis
- Offers compatibility with various input DNA samples

> In this handout, we will focus on ChIP-seq’s application on finding the transcription factor site in the genome. However, the key concept and workflow are similar for identifying histone modification and regulatory non coding sequence. 

## 2. Background Knowledge<a name="232"></a>

The knowledge of some basic biological concepts is necessary for understanding the importance of this method.

#### 1) Transcription Factor<a name="2321"></a>

Sequence-specific transcription factors (TFs) are key regulators of biological processes that function by binding to transcriptional regulatory regions (e.g., promoters, enhancers) to control the expression of their target genes (enhance or repress). Each TF typically recognizes a collection of similar DNA sequences, which can be represented as binding site motifs.<a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5447501/">[3]</a> Therefore, the analysis of regulatory regions in genome sequences is strongly based on the detection of potential transcription factor binding sites. 


![](https://github.com/KylinKang/BENG183/blob/master/How-do-Transcription-Factors-Bind-to-DNA-1.jpg)
![](https://github.com/KylinKang/BENG183/blob/master/OSC_Microbio_11_07_Enhancer.jpg)

[Figure.1](http://pediaa.com/how-do-transcription-factors-bind-to-dna/) The transcription factor binds to the promoter of a gene or other regulatory noncoding sequence like enhancer to control the expression level of the gene. **Figure from How do Transcription Factors Bind to DNA and Method for Predicting Gene Expression by Modeling Transcription Factor Activity.**

#### 2) Gene Regulation and Annotation<a name="2322"></a>

By analyzing whether or not a sequence is bound to TF of interest and evaluating the amount of such TF binding sequence, we gain crucial information about the expression level of the corresponding gene. The information of TF binding site is also important in the discovery and therapy of certain diseases by comparing the gene regulation level among the samples from control and patients. 

The detecting of TF binding site also facillitates gene annotation.It could be realized through detecting transcription-factor binding sites and histone-modification. The chromatin of enhancers was determined and integrative analysis of histone modification and localization profiles of the transcriptional co-activator p300 in human cells was used to find new enhancer <a href="https://docs.google.com/presentation/d/1Va34FmS3-DqZXPqmbybBgL1qgNaUwcGcm86wXHkKrlI/edit#slide=id.p2">[2]</a>.

## 3. Workflow<a name="233"></a>

The following figure reveals an overview of ChIP sequencing workflow. It could be mainly split into three steps: the preparation of sequence library, the pre-filtering of sequencing outcome and the analysis of final result.

![](https://github.com/KylinKang/BENG183/blob/master/Screen%20Shot%202018-12-14%20at%202.20.37%20AM.png)

[Figure.2](https://www.ncbi.nlm.nih.gov/pubmed/22955991) Overview of ChIP-seq workflow and antibody characterization procedures. (A) Steps for which specific ENCODE guidelines are presented in this document are indicated in red. For other steps, standard ENCODE protocols exist that should be validated and optimized for each new cell line/tissue type or sonicator. (*) A commonly used but optional step. **Figure by ChIP-seq guidelines and practices of the ENCODE and modENCODE consortia.**


#### 1) Library Preparation<a name="2331"></a>

There are five steps in library preparation, as presented as Fig.3.

- Crosslink the whole cell to stablize the interaction between DNA and DNA-binding proteins to DNA by treatment of cells with formaldehyde.

- Sonicate DNA to produce sheer chromatin fragments (enzyme digestion could be an alternative).

- Immunoprecipitate by adding an antibody that recognizes a specific transcription factor or histone isoform of interest.
    > The antibody could conjugate with magnetic bead to allow the selection of protein-binding DNA sequence.

- Purify the selected immunocomplex to yield the collection of DNA-protein complex containing the binding site.

- Reverse-crosslink to remove protein and purify DNA.

- Send the built library to sequencing.

> One thing to notice here is that a portion of initial DNA sample is saved for a reference for the immunoprecipitation treated sample to filter the background noise. An alternative way is to treated this reference sample by non-specific transcription factor binding antibody.

![](https://github.com/KylinKang/BENG183/blob/master/nihms-187749-f0001.jpg)

[Figure.3](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2846386/) A detailed workflow of library preparation for ChIP sequencing. **Figure by Insights from genomic profiling of transcription factors.**

#### 2) Sequencing Output Preprocessing<a name="2332"></a>

This step could be divided into two parts:

***1. Preprocessing of fasta/fastq file:***

The quality of output fastq file of sequencing shall first be checked. In general, fastqc is the ideal tool to use here. Quality control occurs when there is Warning or Error in the field of **Per Base Sequence Quality** and **Adapter Content**. Only sequence whose quality score is above a certain threshold, usually 30, could be kept. Also, adapter sequence is filter out.

![](https://github.com/KylinKang/BENG183/blob/master/fastqc.png)

[Figure.4](https://docs.google.com/presentation/d/1Va34FmS3-DqZXPqmbybBgL1qgNaUwcGcm86wXHkKrlI/edit#slide=id.p2) An example of fastqc per base sequence quality output. The ideal quality score should be in the green area, while anything in the red area should be discarded. The per base sequence quality is pretty good in this figure. **Figure by Lecture 6 ChIP-seq-KN.**

>**Commonly Applied Softwares in This Step:**

- Quality Control: [fastqc](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)
- Adapter Removal: [cutadapt](https://cutadapt.readthedocs.io/en/stable/guide.html)

***2. Postfiltering of bam/sam file:***

After quality control, the reads in fastq file are aligned to reference genome. Most aligner would output the overall mapping percentage , as well as individual mapping score for each read. Quality control could also be performed here if needed. The output sam file could be split into three parts:

 - Reads uniquely mapped to one genomic location
 - Reads mapped to multiple genomic locations
 - Reads that could not mapped to any genomic locations.
 
 Usually, since ChIP sequencing is a high throughput method, only the uniquely mapped reads are kept for precision. The bam file could be further sorted and indexed using samtools.

>**Commonly Applied Softwares in This Step:**

- Read Alignment: [STAR](https://github.com/alexdobin/STAR)
- Sam File Processing: [samtools](http://www.htslib.org/)

#### 3) Data Analysis<a name="2333"></a>

***1. Peak Detection:***

The following figure shows different method in ChIP sequencing for peak detection. In this handout, we will focus on the application and processing of peak calling method (MACS2).

![](https://github.com/KylinKang/BENG183/blob/master/nihms705597f2.jpg)

[Figure.5](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4580520/) Outline of three ChIP-seq binding event detection methods. Peak-finding methods (e.g. MACS (Zhang et al., 2008)) typically either shift the ChIP-seq tag locations in a 3′ direction by half the expected fragment length, or extend the length of the tag in a 3′ direction to be equal to the expected fragment length. Tags from opposite strands are merged to construct an unstranded tag density landscapes, and binding event locations are predicted from the locations with maximum tag coverage within each region that contains a significant enrichment of ChIP-seq tags (i.e. the peak summit). **Figure by Protein-DNA binding in high-resolution.**

***2. Motif Discovery:***

![](https://github.com/KylinKang/BENG183/blob/master/annrheumdis-2013-January-72-1-96-F4.large.jpg)

[Figure.6](https://ard.bmj.com/content/72/1/96) Motif finding sample. **Figure by Insights from Genome-wide profiling of target genes for the systemic lupus erythematosus-associated transcription factors IRF5 and STAT4.**

***3. Differential Function Analysis:***

![](https://github.com/KylinKang/BENG183/blob/master/nihms-613746-f0007.jpg)

[Figure.7](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4194139/) A presentation of function/pathway enriched in treated conditon compared to control. **Figure by Insights from A protocol for RNA methylation differential analysis with MeRIP-Seq data and exomePeak R/Bioconductor package.**

>**Commonly Applied Softwares in This Step:**

- Peak Calling and Comparison Across Samples: [MACS2](https://github.com/taoliu/MACS)
- Motif Discovery: [MEME-ChIP](https://www.nature.com/articles/nprot.2014.083)
- Functional Analysis: [DAVID](https://david.ncifcrf.gov/), [Gene Ontology](http://www.geneontology.org/)

## 4. Data Visualization<a name="234"></a> 

**A**<img src="https://github.com/KylinKang/BENG183/blob/master/UCSC.png" alt="drawing" width="600"/>
**B**<img src="https://github.com/KylinKang/BENG183/blob/master/IGV.png" alt="drawing" width="600"/>

[Figure.8](http://genesdev.cshlp.org/content/early/2018/01/10/gad.308536.117.full.pdf) Examples of ChIP sequencing visulization (A: UCSC Browser; B: Integrative Genomics Viewer). **Figure by Transcription factor-dependent ‘anti-repressive’ mammalian enhancers exclude H3K27me3 from extended genomic domains.**

>**Commonly Applied Softwares in This Step:**

- [IGV](http://software.broadinstitute.org/software/igv/UserGuide)
- [UCSC Genome Browser](https://genome.ucsc.edu/cgi-bin/hgGateway)

## 5. Important Application<a name="235"></a> 

**Encode Project**

ChIP sequencing is widely applied in labs which are involved in Encode Project, which aims to delineate all functional elements encoded in the human genome. The binding locations of 119 different DNA-binding proteins and a number of RNA polymerase components in 72 cell types are mapped using ChIP-seq.

The Encyclopedia of DNA Elements (ENCODE) project has systematically mapped regions of transcription, transcription factor association, chromatin structure and histone modification. These data enabled us to assign biochemical functions for 80% of the genome, in particular outside of the well-studied protein-coding regions. Many discovered candidate regulatory elements are physically associated with one another and with expressed genes, providing new insights into the mechanisms of gene regulation. The newly identified elements also show a statistical correspondence to sequence variants linked to human disease, and can thereby guide interpretation of this variation. Overall, the project provides new insights into the organization and regulation of our genes and genome, and is an expansive resource of functional annotations for biomedical research <a href="https://www.ncbi.nlm.nih.gov/pubmed/22955616">[8]</a>.


# Referrence
[1] Robertson, G. et al. Genome-wide profiles of STAT1 DNA association using chromatin immunoprecipitation and massively parallel sequencing. Nat Methods. 2007 Aug; 4(8):651-7.<br>

[2] Zhong, Sheng. Lecture 6_ChIP-seq-KN. BENG 183 FALL 2018.<br>

[3] Sachi Inukai, Kian Hong Kock and Martha L. Bulyk. Transcription factor–DNA binding: beyond binding site motifs. Current Opinion in Genetics & Development, Volume 43, 2017:110-119.<br>

[4] Precise analysis of DNA–protein binding sequences. Illumina.<br>

[5] Arianna Sabò, Theresia R. Kress, Mattia Pelizzola, et al. Selective transcriptional regulation by Myc in cellular growth control and lymphomagenesis. Nature volume 511. 2014 Jun; 488–492.<br>

[6] https://github.com/taoliu/MACS <br>

[7] Wenxiu Ma, William S Noble, Timothy L Bailey. Motif-based analysis of large nucleotide data sets using MEME-ChIP. Nature Protocols volume 9. 2014 May; 1428–1450.<br>

[8] ENCODE Project Consortium. An integrated encyclopedia of DNA elements in the human genome.<br>


