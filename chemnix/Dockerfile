FROM ubuntu:18.04
MAINTAINER Steve Constable <steve.constable@cyclicarx.com>
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y \
    build-essential \
    python2.7 \
    python-numpy \
    python-scipy \
    python-matplotlib \
    python-pandas \
    python-sympy \
    python-nose \
    python-pip \
    openbabel \
    build-essential \
    cmake \
    python-dev \
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
    unzip
ENV RDBASE=/opt/rdkit
ENV LD_LIBRARY_PATH=$RDBASE/lib:$LD_LIBRARY_PATH
ENV PYTHONPATH=$RDBASE:$PYTHONPATH
RUN wget https://github.com/rdkit/rdkit/archive/Release_2018_09_1.tar.gz -O rdkit.tgz \
    && mkdir $RDBASE \
    && tar xzvf rdkit.tgz -C $RDBASE --strip-components 1 \
    && cd $RDBASE \
    && mkdir build \
    && cd build \
    && cmake -DRDK_BUILD_INCHI_SUPPORT=ON .. \
    && make \
    && make install
