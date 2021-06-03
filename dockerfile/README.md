# Build 

    docker build -t lizhen0909/lrece .

or pull from docker hub

# Examples

Suppose there is a fasta/fastq file in $HOME

## Run FLAS 

    docker run  -it --rm -e HOST_USER_ID=$(id -u) -e HOST_USER_GID=$(id -g) -v ~:/data lizhen0909/lrece bash -i -c "cd /data/ && runFLAS.py a.fasta"

## Run LoRMA

    docker run  -it --rm -e HOST_USER_ID=$(id -u) -e HOST_USER_GID=$(id -g) -v ~:/data lizhen0909/lrece bash -i -c "cd /data/ && lorma.sh a.fasta"

## Run cannu to correct/trim seq

    docker run  -it --rm -e HOST_USER_ID=$(id -u) -e HOST_USER_GID=$(id -g) -v ~:/data lizhen0909/lrece bash -i -c "cd /data/ && canu -correct -p ecoli -d ecoli genomeSize=4.8m -pacbio a.fastq "

    docker run  -it --rm -e HOST_USER_ID=$(id -u) -e HOST_USER_GID=$(id -g) -v ~:/data lizhen0909/lrece bash -i -c "cd /data/ && canu -trim -p ecoli -d ecoli genomeSize=4.8m -corrected -pacbio  ecoli/ecoli.correctedReads.fasta.gz " 

## fastq to fasta

    docker run  -it -e HOST_USER_ID=$(id -u) -e HOST_USER_GID=$(id -g) -v ~:/data lizhen0909/lrece bash -i -c "cd /data/ && seqtk seq -A a.fastq > a.fasta"
