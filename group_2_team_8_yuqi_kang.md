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
‘1’, ‘Many’ and ‘All’ indicate how many loci are interrogated in a given experiment. For example, ‘1 versus All’ indicates that the experiment probes the interaction profile between 1 locus and all other potential loci in the genome. ‘All versus All’ means that one can detect the interaction profiles of all loci, genome-wide, and their interactions with all other genomic loci [1].

These kind of specificity is determined by the primer when people use **specific primers** before PCR. 

#### 2) Gene Regulation and Annotation<a name="2322"></a>
Hi-C techniques has the highest through-put (billion reads per sample) but suffering of a relative low resolution of 0.1-1Mb. However, the other methods usually have a higher resolution  around 1kb. For more details one can refer to table2 in [2].

## 3. Workflow<a name="233"></a>
Hi-C is the highest through-put version of 3C-derived technologies. Due to the decreasing cost of 2nd generation sequencing, hi-c is widely used.

The principle of Hi-C can be illustrated as:
![](/assets/hic.gif)
#### 1) Library Preparation<a name="2331"></a>

#### 2) Sequencing Output Preprocessing<a name="2332"></a>

#### 3) Data Analysis<a name="2333"></a>

##### Hi-C critical steps [8] 
- Fixation: keep DNA conformed
- Digestion: enzyme frequency and penetratin
- Fill-in: biotin for junction enrichment
- Ligation: freeze interactions in sequence
- Biotin removal: junctions only
- Fragment size: small fragments sequence better
- Adapter ligation: paired-end and indexing
- PCR: create enough material for flow cell

##### Hi-C derived techniques 
- Hi-C original: [Lieberman-Aiden et al., Science 2010](doi: 10.1126/science.1181369)
- Hi-C 1.0: [Belton-JM et al., Methods 2012](doi: 10.1016/j.ymeth.2012.05.001)
- In situ Hi-C: [Rao et al., Cell 2014](doi: 10.1016/j.cell.2014.11.021)
- Single cell Hi-C: [Nagano et al., Genome Biology 2015](https://doi.org/10.1186/s13059-015-0753-7)
- DNase Hi-C [Ma, Wenxiu, Methods et al](https://www.ncbi.nlm.nih.gov/pubmed/25437436)
- Hi-C 2.0: [Belaghzal et al., Methods 2017](https://www.ncbi.nlm.nih.gov/pubmed/28435001)
- DLO-Hi-C: [Lin et al., Nature Genetics 2018](https://doi.org/10.1038/s41588-018-0111-2)
- Hi-C improving: [Golloshi et al., Methods 2018](https://www.biorxiv.org/content/biorxiv/early/2018/02/13/264515.full.pdf)
- Arima 1-day Hi-C: [Ghurye et al., BioRxiv 2018](https://www.biorxiv.org/content/early/2018/02/07/261149)

## 4. Data Visualization<a name="234"></a> 
ChIA-PET is another method that combines ChIP and pair-end sequencing to analysis the chromtin interaction. It allows for targeted binding factors such as: estrogen receptor alpha, CTCF-mediated loops, RNA polymerase II, and a combination of key architectural factors. on the one hand, it has the benefit of achieving a higher resolution compared to Hi-C, as only ligation products involving the immunoprecipitated molecule are sequenced, on the other hand, ChIA-PET has systematic biases due to ChIP process:
- Only one type of binding factor selected
- Different antibodies
- ChIP conditions


## 5. Important Application<a name="235"></a> 




# Referrence
[1] Robertson, G. et al. "Genome-wide profiles of STAT1 DNA association using chromatin immunoprecipitation and massively parallel sequencing." Nat Methods. 2007 Aug; 4(8):651-7.<br>

[2] Zhong, Sheng. "Lecture 6_ChIP-seq-KN" BENG 183 FALL 2018.<br>

[3] Dekker J, Rippe K, Dekker M, Kleckner N. Capturing chromosome conformation. Science 2002;295(5558):1306–11.<br>

[4] Simonis M, Klous P, Homminga I, Galjaard RJ, Rijkers EJ, Grosveld F, et al. High-res- olution identification of balanced and complex chromosomal rearrangements by 4C technology. Nature Methods 2009;6(11):837–42.<br>

[5] Dostie J, Richmond TA, Arnaout RA, Selzer RR, Lee WL, Honan TA, et al. Chromo- some Conformation Capture Carbon Copy (5C): a massively parallel solution for mapping interactions between genomic elements. Genome Res 2006;16(10): 1299–309.<br>

[6] Lieberman-Aiden E, van Berkum NL, Williams L, Imakaev M, Ragoczy T, Telling A, et al. Comprehensive mapping of long-range interactions reveals folding principles of the human genome. Science 2009;326(5950):289–93.<br>

[7] Fullwood, M.J. et al. (2009) An oestrogen-receptor-alpha-bound human chromatin interactome. Nature 462, 58–64.<br>

[8] https://github.com/hms-dbmi/hic-data-analysis-bootcamp/blob/master/HiC-Protocol.pptx.


