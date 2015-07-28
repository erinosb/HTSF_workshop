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
  
I have already written the code for you in a script called **script06_htseq-count.sh***. This script loops through every sample and counts all reads associated with the gene models in the human genome annotation file (a .gtf document).


```
# NAVIGATE TO <yourversion>/01_RNASeqDemo/05_scripts
# EXECUTE THE CODE:
$ pwd
$ bsub -q week -n 1 -o ../00_logs/%J_htseqcount.log "bash script06_htseq-count.sh"  
```

To see what happened
+ read the log file
+ Look at the output of htseq-counts in `/04\_results/htseqcounts/`

**Homework** 
+ Try running script06_htseq-count.sh when you have all the tophat alignments completed.
+ Try running script07\_merge\_htseqcounts.sh
+ Inspect the merged output file \<yourversion\>/04\_results/htseqcounts/merge\_counts.txt





