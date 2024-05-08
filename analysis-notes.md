# Chapter 2: Raw data

## Download from ENA
The analysis uses data from **"ERP004763"**. To download the fastq files on my node in the server, first I downloaded the script to download all the files from ENA, which looks like this:
```
(base)$ head downloadENA.txt
wget -nc ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR458/ERR458579/ERR458579.fastq.gz
wget -nc ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR459/ERR459115/ERR459115.fastq.gz
wget -nc ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR458/ERR458636/ERR458636.fastq.gz
wget -nc ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR458/ERR458785/ERR458785.fastq.gz
wget -nc ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR458/ERR458984/ERR458984.fastq.gz
```
As before, the "ftp" is not accessible on my server, so based on suggestion I needed to change them all to "https", so what I did was:
```
(base)$ awk '{sub("ftp:","https:")}1' downloadENA.txt > downloadENAmodified.sh

# OUTPUT
(base)$ head downloadENAmodified.sh
wget -nc https://ftp.sra.ebi.ac.uk/vol1/fastq/ERR458/ERR458579/ERR458579.fastq.gz
wget -nc https://ftp.sra.ebi.ac.uk/vol1/fastq/ERR459/ERR459115/ERR459115.fastq.gz
wget -nc https://ftp.sra.ebi.ac.uk/vol1/fastq/ERR458/ERR458636/ERR458636.fastq.gz
wget -nc https://ftp.sra.ebi.ac.uk/vol1/fastq/ERR458/ERR458785/ERR458785.fastq.gz
wget -nc https://ftp.sra.ebi.ac.uk/vol1/fastq/ERR458/ERR458984/ERR458984.fastq.gz
```
Since download would take a long time, I opened a "tmux" session, `chmod +x` the file and then let it run on the background (`./downloadENAmodified.sh` and then exiting the session).

