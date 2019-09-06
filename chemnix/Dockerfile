FROM ubuntu:18.04
MAINTAINER Steve Constable <steve.constable@cyclicarx.com>
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y \
    build-essential \
    python3-numpy \
    python3-scipy \
    python3-matplotlib \
    python3-pandas \
    python3-sympy \
    python3-nose \
    python3-pip \
    openbabel \
    libopenbabel-dev \
    swig \
    cmake \
    python3-dev \
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
    && cmake -DRDK_BUILD_INCHI_SUPPORT=ON -DPYTHON_EXECUTABLE=/usr/bin/python3 -DPYTHON_INCLUDE_DIR=/usr/include/python3.6m -DPYTHON_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython3.6m.so .. \
    && make \
    && make install
