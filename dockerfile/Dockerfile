# docker build -t lizhen0909/lrece .
FROM ubuntu:18.04

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


RUN apt-get install bzip2 libboost1.62-all-dev zlib1g-dev -y


# env python2.7
RUN  /opt/conda/bin/conda create  -c bioconda --name lrece python=2.7 htslib=1.3.1 minimap2=2.17 seqtk=1.3 sra-tools=2.9.1 pbh5tools=0.8.0 poretools=0.6.1a1 samtools=1.7 && \
    /opt/conda/bin/conda clean -tipsy && \
    echo "conda activate lrece" >> ~/.bashrc && \
    echo "alias l='ls -alrt'" >> ~/.bashrc      && \
    echo "alias h='history'" >> ~/.bashrc      && \
    echo "set -o vi" >> ~/.bashrc


#FLAS
RUN ls && git clone https://github.com/bochen0909/MECAT.git && cd MECAT && make && cp -r Linux-amd64/bin/* /usr/bin/
RUN ls && git clone https://github.com/bochen0909/FLAS.git && cd FLAS && make && cp -r bin/* /usr/bin/ && cp runFLAS.py /usr/bin/

RUN apt-get install cmake -y



RUN wget https://www.cs.helsinki.fi/u/lmsalmel/LoRMA/LoRMA-0.4.tar.gz && tar xf LoRMA-0.4.tar.gz && cd LoRMA-0.4/ && mkdir build && cd build && cmake .. && make && cp lorma.sh /usr/bin/ && cp LoRMA /usr/bin/

RUN wget https://gite.lirmm.fr/lordec/lordec-releases/uploads/2565309db279a68b6dc50071a0a709a7/lordec-src_0.7.tar.gz && tar xf lordec-src_0.7.tar.gz && cd lordec-src_0.7/ && make && mkdir /usr/bin/lordec && cp lordec-correct lordec-stat lordec-trim lordec-trim-split  lordec-build-SR-graph /usr/bin/ && \
cp lordec-correct lordec-stat lordec-trim lordec-trim-split  lordec-build-SR-graph /usr/bin/lordec/

RUN cd /usr/bin/ && ln -s lordec LoRDEC


RUN ls -alrt /usr/bin/

CMD [ "/bin/bash" ]
