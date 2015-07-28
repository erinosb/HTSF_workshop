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

We will need htseq-counts, and r

```
#EXECUTE THESE COMMANDS
$ module load htseq-counts
$ module load r
```

#### HT-seq counts

Will read as input an accepted_hits_bam file from tophat.

```
htseq-count \                                           # Literally call htseq-count
    --format=bam \                                      # input format of the incoming file is bam
    --order=pos \                                       # .bam file has been ordered
    --stranded=no \                                     # RNA-seq is NOT stranded
    --minaqual=20 \                                     # Throw out any alignments with minquality scores less than 20
    --type=exon \                                       # Use concatenated exons as "genes"
    --mode=union                                        # Run in "union" mode   
    ../04_results/tophat/${file}_opd/accepted_hits.bam \      # Here is the place to put the output
    /proj/seq/data/HG19_UCSC/Annotation/Genes/genes.gtf \     # Here is the .gtf annotation file
    1> ../04_results/htseqcounts/${file}_counts.txt           # Here is the input, a .bam file from tophat
```
  
