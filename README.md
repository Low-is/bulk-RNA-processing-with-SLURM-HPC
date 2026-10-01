# bulk_rna_processing using SLURM (HPC)

## WSL and Ubuntu Installation
```
# WindowsPowerShell

wsl --install
wsl --install -d Ubuntu
```

## Run Ubuntu
```
# WindowsPowerShell
wsl -d Ubuntu

# Will ask to create user name and password...
# Press `ENTER` for username
# Create simple password, nothing will appear on the screen, no dots or asterisks. This is normal for Linux
```


## Determined read length of trimmed FASTQ files
```
# Ubuntu

zcat /mnt/d/Projects/animal_projects/animal_brain/Lauren_Jantzie_RNASeq/LJO1JHU504_striatum/fastq/127791_5_R1.trimmed.fastq.gz | awk 'NR==2 {print length($0); exit}'

# If output: 150
# --sjdbOverhang 149

# If output: 100
# --sjdbOverhang 99
```


## Build STAR index
```
# Ubuntu

STAR \
  --runThreadN 16 \
  --runMode genomeGenerate \
  --genomeDir ~/genomes/h38/STAR \
  --genomeFastaFiles ~/genomes/h38/Homo_sapiens.GRCh38.dna.primary_assembly.fa \
  --sjdbGTFfile ~/genomes/h38/Homo_sapiens.GRCh38.99.gtf \
  --sjdbOverhang 149


# Or try:


STAR \
  --runThreadN 16 \
  --runMode genomeGenerate \
  --genomeDir ~/genomes/h38/STAR \
  --genomeFastaFiles ~/genomes/h38/Homo_sapiens.GRCh38.dna.primary_assembly.fa \
  --sjdbGTFfile ~/genomes/h38/Homo_sapiens.GRCh38.99.gtf \
  --sjdbOverhang 149 \
  --genomeSAindexNbases 13
```


python bulk_rna_processing.py
```
