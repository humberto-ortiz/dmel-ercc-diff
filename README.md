# dmel-ercc-diff

Using Drosophila melanogaster spike-in data to refine diferential
expression algorithms.

2015/03/12 - HOZ

Detection of differential expression from de-novo RNASeq data.

A common bioinformatics problem is the detection of differential
expression in two samples. When the data is from an RNASeq experiment
the procedure is usually to map reads to a reference genome, e.g. using
bowtie[1]. When no reference genome exists, a de-novo assembly is
generated from the reads first[2], then the reads are mapped again to
the artificial reference produced by concatenating the contigs from the
de-novo assembly.

K-mer counting is a pre-processing step that is used prior to de-novo
assembly to normalize the sequence data and remove some errors [3].

An alternative strategy could be to create a de Bruijn graph where the
edges have an associated count of occurrences in the two samples. The
full graph can be examined to detect regions of differential expression, and only those contigs assembled.

For the summer project, the student can use simulated reads, like those
generated with flux-simulator[4], to detect differential expression.
Once the software pipeline is designed, we can apply the pipeline to a
spike-in experiment with known concentrations of Drosophila and foreign
RNA, as described in [5].

At the UPR, several groups are doing de-novo RNAseq in non-model
organisms, and this project could provide tools to help these projects.

[1] http://genomebiology.com/2009/10/3/R25
[2] http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3571712/
[3] http://arxiv.org/abs/1203.4802
[4] http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3488205/
[5] http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3166838/


2014/09/09 - HOZ

We have a single repetition of 5% and 1%, but a bunch of 2.5%

5% ERCC in dmel S2

GSM517059  100ng_S2_5ng_ERCC_phaseV_pool15_mRNA-seq

2.5% ERCC in dmel S2

GSM517060 100ng_S2_2.5ng_ERCC_phaseV_pool15_mRNA-seq

GSM516588 100ng_library_methA_S2_2.5%ERCC_phaseV_pool15mRNA
GSM516589 100ng_library_methB_S2_2.5%ERCC_phaseV_pool15_mRNA
GSM516590 50ng_library_methB_S2_2.5%ERCC_phaseV_pool15_mRNA
GSM516591 10ng_library_methB_S2_2.5%ERCC_phaseV_pool15_mRNA
GSM516592 1ng_library_methB_S2_2.5%ERCC_phaseV_pool15_mRNA
GSM516593 0.4ng_library_methB_S2_2.5%ERCC_phaseV_pool15_mRNA
GSM516594 0.01ng_library_methB_S2_2.5%ERCC_phaseV_pool15_mRNA

1% ERCC in dmel S2

GSM517061  100ng_S2_1ng_ERCC_phaseV_pool15_mRNA

2015/05/12 - HOZ

SRA links for GSE20579

http://www.ncbi.nlm.nih.gov/sra?linkname=bioproject_sra_all&from_uid=125273

GSM517059: 100ng_S2_5ng_ERCC_phaseV_pool15_mRNA-seq - SRX019234

http://www.ncbi.nlm.nih.gov/sra/SRX019234%5Baccn%5D

ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR039/SRR039933/SRR039933.sra

GSM517061: 100ng_S2_1ng_ERCC_phaseV_pool15_mRNA - SRX019236

http://www.ncbi.nlm.nih.gov/sra/SRX019236%5Baccn%5D

ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR039/SRR039935/SRR039935.sra

Bioproject for GSE20555

http://www.ncbi.nlm.nih.gov/bioproject/?term=GSE20555

SRA links for GSM16588-94 are here:

http://www.ncbi.nlm.nih.gov/sra?linkname=bioproject_sra_all&from_uid=125199

GSM516588 - 100ng_library_methA_S2_2.5%ERCC_phaseV_pool15mRNA - SRX018870

http://www.ncbi.nlm.nih.gov/sra/SRX018870%5Baccn%5D

ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR039/SRR039458/SRR039458.sra

GSM516590 - 50ng_library_methB_S2_2.5%ERCC_phaseV_pool15_mRNA - SRX018872

ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR039/SRR039460/SRR039460.sra

http://www.ncbi.nlm.nih.gov/bioproject/?term=GSE20579

The 4 ftp files are SRA files for 5%, 1%, 2.5%, 2.5% ERCC spike ins.

The files can be read (and dumped to fasta/fastq format) with the SRA toolkit:

http://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/current/

```
$ grep "^ftp" README.md > getit
$ wget -ci getit 
```
