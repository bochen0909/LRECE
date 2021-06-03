Suppose there is a fasta file in $HOME

Run FLAS 

docker run  -it -e HOST_USER_ID=$(id -u) -e HOST_USER_GID=$(id -g) -v ~:/data lizhen0909/lrece bash -i -c "cd /data/ && runFLAS.py a.fasta"
