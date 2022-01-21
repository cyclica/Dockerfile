# version: 20220121
FROM ubuntu:20.04
MAINTAINER Steve Constable <steve.constable@cyclicarx.com>
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y locales
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    locale-gen
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
RUN apt-get install -y \
    build-essential \
    python3-numpy \
    python3-scipy \
    python3-sympy \
    python3-nose \
    python3-pip \
    openbabel \
    swig \
    cmake \
    git \
    python3-dev \
    libboost1.67-all-dev \
    sqlite3 \
    libsqlite3-dev \
    libfreetype6-dev \
    wget \
    unzip
ENV RDBASE=/opt/rdkit
ENV LD_LIBRARY_PATH=$RDBASE/lib:$LD_LIBRARY_PATH
ENV PYTHONPATH=$RDBASE:$PYTHONPATH
RUN wget https://github.com/rdkit/rdkit/archive/Release_2021_09_4.tar.gz -O rdkit.tgz \
    && mkdir $RDBASE \
    && tar xzvf rdkit.tgz -C $RDBASE --strip-components 1 \
    && cd $RDBASE \
# patch to modify the font file hash from the old value to the new value
    && sed -i 's/23ed3f833c1ae0adb141a26b4a30d73e/850b0df852f1cda4970887b540f8f333/g' Code/GraphMol/MolDraw2D/CMakeLists.txt \
    && mkdir build \
    && cd build \
    && cmake -DRDK_BUILD_INCHI_SUPPORT=ON -DPYTHON_EXECUTABLE=/usr/bin/python3 -DPYTHON_INCLUDE_DIR=/usr/include/python3.8 -DPYTHON_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython3.8.so .. \
    && make -j 13 \
    && make install
