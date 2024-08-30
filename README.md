# An orphan viral genome with unclear evolutionary status sheds light on a distinct lineage of flavi-like virus infecting plants

## Section1: Small RNA analysis (Or vsiRNAs analysis here)
### step1: Download the public datasets from NCBI SRA database
#### Replace the path to your own. Take the SRR14064437 as an example.
```
#Get the download link from ebi.ac.uk: 'ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR778/007/SRR7784727/SRR7784727.fastq.gz' 
/public/home/xuzhongtian/.aspera/connect/bin/ascp  -v -QT -l 400m -P 33001 -k 1 -i /public/home/xuzhongtian/.aspera/connect/etc/asperaweb_id_dsa.openssh  era-fasp@fasp.sra.ebi.ac.uk:/vol1/fastq/SRR778/007/SRR7784727/SRR7784727.fastq.gz .
```
