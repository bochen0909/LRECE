# docker build -t lizhen0909/lrece .
FROM ubuntu:16.04

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

RUN apt-get update --fix-missing && \ 
    apt-get install -y software-properties-common vim build-essential wget  \
	git && \
    ls
    #apt-get clean && \
    #rm -rf /var/lib/apt/lists/*


#install conda 
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-py37_4.9.2-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda clean -tipsy && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc 


RUN apt-get install bzip2

# env python3.7
RUN  /opt/conda/bin/conda create  -c bioconda --name python3 python=2.7 minimap2 seqtk sra-tools=2.9.1 pbh5tools poretools samtools && \
    /opt/conda/bin/conda clean -tipsy && \
    echo "conda activate python3" >> ~/.bashrc && \
    echo "alias l='ls -alrt'" >> ~/.bashrc      && \
    echo "alias h='history'" >> ~/.bashrc      && \
    echo "set -o vi" >> ~/.bashrc



CMD [ "/bin/bash" ]
