## An orphan viral genome with unclear evolutionary status sheds light on a distinct lineage of flavi-like virus infecting plants
***

## Part1: Small RNA analysis (Or vsiRNAs analysis here)
### step1: Download the public datasets from NCBI SRA database
#### Replace the path to your own. Take the SRR14064437 as an example.
```
#Get the download link from ebi.ac.uk: 'ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR778/007/SRR7784727/SRR7784727.fastq.gz' 
/public/home/xuzhongtian/.aspera/connect/bin/ascp  -v -QT -l 400m -P 33001 -k 1 -i /public/home/xuzhongtian/.aspera/connect/etc/asperaweb_id_dsa.openssh  era-fasp@fasp.sra.ebi.ac.uk:/vol1/fastq/SRR778/007/SRR7784727/SRR7784727.fastq.gz .
```

### step2: Quality control process (Remove the adapter region in the raw reads).
```
cutadapt -a "AGATCGGAAGA"  $data_path/${file}.fq.gz  -j 112 -o SRR7784727.clean.fastq --untrimmed-output SRR7784727.notfound.fastq --minimum-length 8
```

### step3: Quality control process (Remove the ambiguous reads containing 'N'; keep the reads with lengths between 18 and 30 nucleotides; collapse the reads with the same sequence to unique sequences)
```
# The script used below is an in-house script written by Zhongtian Xu. 
python sRNAs_collapse2unique.py SRR7784727.clean.fastq
```
### step4: virus identification by VirusDetect (Zheng et al. 2017). 
```
# The script 'sRNAs_collapse2unique.py' not only generates unique small RNA reads with abundance annotation but also generates single clean reads that could be used as input for VirusDetect.
perl virus_detect.pl --reference known_virus_reference  --thread_num 60 SRR7784727.clean.forVelvetAssembly.fasta
```

### Reference:
+ Zheng Y, Gao S, Padmanabhan C, Li R, Galvez M, Gutierrez D, Fuentes S, Ling KS, Kreuze J, Fei Z. VirusDetect: An automated pipeline for efficient virus discovery using deep sequencing of small RNAs. Virology. 2017 Jan;500:130-138.
