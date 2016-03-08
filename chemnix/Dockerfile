FROM ubuntu:14.04
MAINTAINER Lenny Morayniss <leonard.morayniss@cyclicarx.com
RUN apt-get update && apt-get install -y \
    python2.7 \
    python-numpy \
    python-scipy \ 
    python-matplotlib \
    ipython \
    ipython-notebook \
    python-pandas \
    python-sympy \
    python-nose \
    python-pip \
    openbabel \
    build-essential \
    cmake python-dev \
    libboost-dev \
    libboost-python-dev \
    libboost-regex-dev \
    rdkit-data \
    gcc \
    git \
    wget \
    unzip
ENV RDBASE=/opt/rdkit/
ENV LD_LIBRARY_PATH=$RDBASE/lib:$LD_LIBRARY_PATH
ENV PYTHONPATH=$RDBASE:$PYTHONPATH
RUN wget https://sourceforge.net/projects/rdkit/files/latest/download?source=files -O rdkit.tgz \
    && tar xzvf rdkit.tgz -C /opt \
    && mv /opt/`ls /opt/` /opt/rdkit/ \
    && . ~/.bashrc \
    && cd $RDBASE/External/INCHI-API/ \
    && ./download-inchi.sh \
    && cd $RDBASE \
    && mkdir build \
    && cd build \
    && cmake -DRDK_BUILD_INCHI_SUPPORT=ON .. # to install InChI generation code \
    && make -j 8 # to use multiple processors \
    && make install
