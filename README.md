<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#gencode---cls-master-table">Gencode - CLS Master TableAbout The Project</a> </li>
    <li><a href="#background">Background</a></li>
    <li>
      <a href="#master-tables">Master Tables</a>
      <ol>
        <li><a href="#attributes-specifics">Attributes specifics</a>
          <ol>
            <li><a href="#samples-metadata">Samples Metadata</a></li>
            <li><a href="#tissue-codes">Tissue Codes</a></li>
          </ol>
        </li>
      </ol>
    </il>
    <li><a href="#quickstart">Quickstart</a></il>
    </lo>
</details>

# Gencode - CLS Master Table
Here we specifically report on the results of the GENCODE pipeline to produce a collection of full length high quality transcript. 

# Background
We employed CLS to target genomic regions with apparently weak, but potentially relevant, transcriptional activity. These include, among others, regions predicted to encode lncRNAs, enhancers, precursors of small RNAs, RNAs predicted to contain structural motifs, host non-coding GWAS hits or regions showing evolutionary characteristics of protein coding gene, or that are evolutionary conserved. Probes were designed in the human genome version hg38 using gencode v27 as reference annotation, and RNA has been captured in multiple matched adult and embryonic tissues in both human and mouse. All long RNAseq reads have been processed using [LyRic](https://github.com/guigolab/LyRic), employing short read RNAseq data to support long reads derived transcript models.

# Master Tables
The tables follow the canonical GTF format.

1. Human:
2. Mouse:

# Attributes specifics
Each feature in the table is associated to a gene_id and transcript_id attributes, specifying the unique identifier as generated by LyRic.
The `transcript` features are additionally endowed with the following attributes:
||||
|-|-|-|
1 | target | comma-separated list of the genomic regions targeted by the pipeline. For each target we report, in order, the *source database*, the *identifier* in the aforementioned db, the *chromosome*, *start* and *end* coordinates, and the *strand*.
2 | endSupport | a value among **polyAOnlySupported**, **cageOnlySupported**, **cagePolyASupported**, **noCageNoPolyASupported**, indicating the type of support available for the transcript model.
3 | spliced | either **spliced** or **unspliced**, indicating whether the associated transcript model is composed of different exons or remains unspliced.
4 | refCompare | result of gffcompare against Gencode annotation *v24*. The original codes have been further collapsed to obtain the follwing categories: **Antisense** (corresponding gff codes *s, x*), **Equal** (*=*), **Extends** (*k*), **Included** (*c*), **Intergenic** (*y,p,u*), **Intronic** (*i*), **Overlaps** (*j,e,m,o,n*).
5 | currentCompare | result of gffcompare against Gencode annotation *v41* (same categories as before). 
6 | sampleN | integer value indicating the number of samples in which these transcript was encountered.
7 | samplesMetadata | a list of mnemotechnics unique sample IDs. See [Samples Metadata](#samples-metadata)
8 | expression | decimal value corresponding to the level of the expression of the transcript in the given sample, expressed as RPM.

# Samples Metadata
The samples IDs have been generated in a way to keep track of as many metadata as possible. The names are composed as follows:
|||||
|-|-|-|-|
0 | Sample ID | Fixed prefix | SID
1 | Organism | Single letter code for the organism | **H** (human), **M** (mouse)
2 | Tissue | Two letter code indicating the tissue | See [Tissue codes](#tissue-codes)
3 | Stage  | Single letter code for the stage | **A** (adult), **E** (embryo), **P** (placenta)
4 | Sequencing Technology | Single letter code for the sequencing technology | **O** (Oxford-nanopore), **P** (PacBio)
5 | Capture status  | Single letter code for capture | **P** (pre-capture), **C** (post-capture)
6 | Biological Replica | Two digit code for the biological replica | - |
7 | Technical Replica | Two digit code for the technical replica | - |

# Tissue Codes
|||
|-|-|
Brain | Br
Heart | He
Liver | Li
WBCs | Wb
ESC | Wb
iPSC | Wb
Testis | Te
Placenta | Pl
Tpool | Tp
Cpool | Cp

Some examples of aliases and their meaning
 * SIDMBrEPP0101: SID mouse brain embryo pacbio precaptur biologicalReplicate01 technicalReplicate01
 * SIDHWbAOC0103: SID human whiteBlood adult ont postcaptur biologicalReplicate01 technicalReplicate03
 * SIDHPlPPP0202: SID human placenta placenta pacbio precaptur biologicalReplicate02 technicalReplicate02

# Quickstart
The following script is readily available to [extract the tags](https://github.com/abreschi/utils/blob/master/extract.gtf.tags.sh) from the GTF file.
