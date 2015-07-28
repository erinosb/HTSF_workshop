# RNA-seq Count

Welcome to an introduction of RNA-seq analysis, a part of the High Throughput Sequencing Facility introduction to Deep Sequencing Analysis.

____

## Setup

#### Log into killdevil using your X11 or Xquartz options.

MAC Users
1. Open XQuartz
2. Login using `ssh -Y <youronyen>@killdevil.unc.edu

PC Users

#### Load modules

We will need htseq-counts, r, 

htseq-count --format=bam --order=pos --stranded=no --minaqual=20 --type=exon --mode=union ../04_results/tophat/${file}_opd/accepted_hits.bam /proj/seq/data/HG19_UCSC/Annotation/Genes/genes.gtf 1> ../04_results/htseqcounts/${file}_counts.txt
  
