# Handout -- ChIP Sequencing
1. [Introduction](#231)
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

> In this handout, we will focus on ChIP-seq’s application on finding the transcription factor site in the genome. However, the key concept and workflow are similar for identifying histone modification and regulatory non coding sequence. 

## 2. Background Knowledge<a name="232"></a>

The knowledge of some basic biological concepts is necessary for understanding the importance of this method.

#### 1) Transcription Factor<a name="2321"></a>

Sequence-specific transcription factors (TFs) are key regulators of biological processes that function by binding to transcriptional regulatory regions (e.g., promoters, enhancers) to control the expression of their target genes (enhance or repress). Each TF typically recognizes a collection of similar DNA sequences, which can be represented as binding site motifs.<a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5447501/">[3]</a> Therefore, the analysis of regulatory regions in genome sequences is strongly based on the detection of potential transcription factor binding sites. 

![](https://github.com/KylinKang/BENG183/blob/master/How-do-Transcription-Factors-Bind-to-DNA-1.jpg)
![](https://github.com/KylinKang/BENG183/blob/master/OSC_Microbio_11_07_Enhancer.jpg)
Figure.1: The transcription factor binds to the promoter of a gene or other regulatory noncoding sequence like enhancer to control the expression level of the gene. **Figure from How do Transcription Factors Bind to DNA and Method for Predicting Gene Expression by Modeling Transcription Factor Activity.**

#### 2) Gene Regulation and Annotation<a name="2322"></a>

By analyzing whether or not a sequence is bound to TF of interest, we gain crucial information about the expression level of the corresponding gene. The information of TF binding site is also important in the discovery and therapy of certain diseases. The detecting of TF binding site also facillitates gene annotation.

Genome annotation could also be realized through detecting transcription-factor binding sites and histone-modification. The chromatin of enhancers was determined and integrative analysis of histone modification and localization profiles of the transcriptional co-activator p300 in human cells was used to find new enhancer <a href="https://docs.google.com/presentation/d/1Va34FmS3-DqZXPqmbybBgL1qgNaUwcGcm86wXHkKrlI/edit#slide=id.p2">[2]</a>.

## 3. Workflow<a name="233"></a>

#### 1) Library Preparation<a name="2331"></a>

#### 2) Sequencing Output Preprocessing<a name="2332"></a>

#### 3) Data Analysis<a name="2333"></a>



## 4. Data Visualization<a name="234"></a> 


## 5. Important Application<a name="235"></a> 




# Referrence
[1] Robertson, G. et al. Genome-wide profiles of STAT1 DNA association using chromatin immunoprecipitation and massively parallel sequencing. Nat Methods. 2007 Aug; 4(8):651-7.<br>

[2] Zhong, Sheng. Lecture 6_ChIP-seq-KN. BENG 183 FALL 2018.<br>

[3] Sachi Inukai, Kian Hong Kock and Martha L. Bulyk. Transcription factor–DNA binding: beyond binding site motifs. Current Opinion in Genetics & Development, Volume 43, 2017:110-119.<br>

[4] Simonis M, Klous P, Homminga I, Galjaard RJ, Rijkers EJ, Grosveld F, et al. High-res- olution identification of balanced and complex chromosomal rearrangements by 4C technology. Nature Methods 2009;6(11):837–42.<br>

[5] Dostie J, Richmond TA, Arnaout RA, Selzer RR, Lee WL, Honan TA, et al. Chromo- some Conformation Capture Carbon Copy (5C): a massively parallel solution for mapping interactions between genomic elements. Genome Res 2006;16(10): 1299–309.<br>

[6] Lieberman-Aiden E, van Berkum NL, Williams L, Imakaev M, Ragoczy T, Telling A, et al. Comprehensive mapping of long-range interactions reveals folding principles of the human genome. Science 2009;326(5950):289–93.<br>

[7] Fullwood, M.J. et al. (2009) An oestrogen-receptor-alpha-bound human chromatin interactome. Nature 462, 58–64.<br>

[8] https://github.com/hms-dbmi/hic-data-analysis-bootcamp/blob/master/HiC-Protocol.pptx.


