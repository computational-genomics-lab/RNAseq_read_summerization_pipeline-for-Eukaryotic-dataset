# RNAseq_read_summerization_pipeline-for-Eukaryotic-dataset
Snakemake pipeline for eukaryotic RNAseq data analysis which assigns the genomic features to the mapped (cleaned and filtered) reads that were generated from RNA sequencing experiment (raw reads)


This pipeline performs RNAseq read summerization for Eukaryotic dataset through counting mapped reads for genomic features in the following steps:

1. Quality-trimming, filtering and adapter-trimming of the input raw Illumina reads using bbduk (rule clean)
2. Indexing of the provided refernce whole genome using the corresponding annotation file through STAR (rule index_build)
3. Alignment of the trimmed, filtered reads to the indexed reference genome using STAR aligner and sorting of the output BAM file according to the genomic coordinates (rule map)
4. Read summarization through counting mapped reads for genomic features (CDS for example) using featurecounts (rule featurecounts)
5. Genome annotation file of the provided reference genome and the sorted BAM file with their path will be required for step 4 (rule featurecounts in the snakemake program)
6. After obtaining the count file form this pipeline, use deseq2 separately for differential gene expression analysis 

Modify the given path of the input and output files written in the snakemake file to the appropriate user's path. The path /home/sutripa/heatShock/ is mentioned as an example.

# Software/package/tool required to install

1. Snakemake
2. bbduk
3. bowtie
4. samtools
5. featurecounts

# command to run the pipeline
snakemake --snakefile Eu_rnaseq_rawreads-to-countdata --core 40
   
