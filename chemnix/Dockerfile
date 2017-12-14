FROM ubuntu:16.04
MAINTAINER Lenny Morayniss <leonard.morayniss@cyclicarx.com>

RUN apt-get update && apt-get install -y python-software-properties \
    software-properties-common

RUN add-apt-repository ppa:jonathonf/python-3.6 && apt-get update

RUN apt-get install -y python3.6 \
    python3.6-dev \
    python3-pip \
    python3.6-venv \
    openbabel \
    build-essential \
    cmake \
    libboost-dev \
    libboost-python-dev \
    libboost-regex-dev \
    rdkit-data \
    gcc \
    git \
    sqlite3 \
    libsqlite3-dev \
    libboost-system-dev \
    libboost-thread-dev \
    libboost-serialization-dev \
    wget \
    unzip \
    python3-numpy \
    python3-scipy \
    python3-matplotlib \
    ipython3 \
    ipython3-notebook \
    python3-pandas \
    python3-sympy \
    python3-nose 

ENV RDBASE=/opt/rdkit
ENV LD_LIBRARY_PATH=$RDBASE/lib:$LD_LIBRARY_PATH
ENV PYTHONPATH=$RDBASE:$PYTHONPATH
RUN wget https://github.com/rdkit/rdkit/archive/Release_2016_09_4.tar.gz -O rdkit.tgz \
    && mkdir  $RDBASE \
    && tar xzvf rdkit.tgz -C $RDBASE --strip-components 1 \
    && cd $RDBASE \
    && mkdir  build \
    && cd build \
    && cmake -DRDK_BUILD_INCHI_SUPPORT=ON  -DPYTHON_EXECUTABLE='/usr/bin/python3.6'  -DPYTHON_INCLUDE_DIR='/usr/include/python3.6' -DPYTHON_LIBRARY='/usr/lib/python3.6'  -D PYTHON_NUMPY_INCLUDE_PATH='/usr/lib/python3/dist-packages/numpy/core/include' .. \
    && make -j4 \
    && make -j4 install
