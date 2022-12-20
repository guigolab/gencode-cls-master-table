# Gencode-cls-master-table
Here we specifically report on the results of the GENCODE pipeline to produce a collection of full length high quality transcript. 

# Background
We employed CLS to target genomic regions with apparently weak, but potentially relevant, transcriptional activity. These include, among others, regions predicted to encode lncRNAs, enhancers, precursors of small RNAs, RNAs predicted to contain structural motifs, host non-coding GWAS hits or regions showing evolutionary characteristics of protein coding gene, or that are evolutionary conserved. Probes were designed in the human genome version hg38 using gencode v27 as reference annotation, and RNA has been captured in multiple matched adult and embryonic tissues in both human and mouse. All long RNAseq reads have been processed using [LyRic](https://github.com/guigolab/LyRic), employing short read RNAseq data to support long reads derived transcript models.

# Master Tables
The tables follow the canonical GTF format.

1. Human:
2. Mouse:

# Attributes specifics
Each feature in the table is associated to a gene_id and transcript_id attributes, specifying the unique identifier as generated by LyRic.
The `transcript` feature are additionally endowed with the following attributes:
||||
|-|-|-|
1 | target | comma-separated list of the genomic regions targeted by the pipeline. For each target we report, in order, the `source database`, the `identifier` in the aforementioned db, the `chromosome`, `start` and `end` coordinates, and the `strand`.
2 | endSupport | a value among `polyAOnlySupported`,`cageOnlySupported`,`cagePolyASupported`, `noCageNoPolyASupported`, indicating the type of support available for the transcript model.
3 | spliced | either `spliced` or `unspliced`, indicating whether the associated transcript model is composed of different exons or remains unspliced.
4 | refCompare | result of gffcompare against Gencode annotation v24. The original codes have been further collapsed to obtain the follwing categories: Antisense (corresponding gff codes `s`, `x`), Equal (`=`), Extends (`k`), Included (`c`), Intergenic (`y`,`p`,`u`), Intronic (`i`), Overlaps (`j`, `e`, `m`, `o`, `n`).
5 | currentCompare | result of gffcompare against Gencode annotation v41 (same categories as before). 
6 | sampleN | integer value indicating the number of samples in which these transcript was encountered.
7 | samplesMetadata | a list of mnemotechnics unique sample IDs (elaborated in ...)
8 | expression | decimal value corresponding to the level of the expression of the transcript in the given sample, expressed as RPM.

# Samples Metadata
