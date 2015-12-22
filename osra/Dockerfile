FROM ubuntu:14.04
MAINTAINER Leonard Morayniss <leonard.morayniss@cyclicarx.com>
RUN apt-get update && apt-get install -y \
    gcc \
    g++ \
    make \
    lzip \
    curl \
    wget \
    libtclap-dev \
    libpotrace0  \
    libpotrace-dev  \
    libocrad-dev \
    openbabel \
    libopenbabel-dev  \
    libgraphicsmagick++-dev \
    libnetpbm10-dev \
&&  apt-get clean \
&&  rm -rf /var/lib/lists/*
ENV CXXFLAGS -pthread 
RUN mkdir -p /tmp/OSRA \
    && curl http://ftp.gnu.org/gnu/ocrad/ocrad-0.25.tar.lz \
    | tar --lzip -xC /tmp/OSRA \
    && cd /tmp/OSRA/ocrad-0.25 \
    && ./configure \
    && make \
    && make install
RUN mkdir -p /tmp/OSRA \
    && curl http://cactus.nci.nih.gov/osra/gocr-0.50pre-patched.tgz \
    | tar -xzC /tmp/OSRA \
    && cd /tmp/OSRA/gocr-0.50pre-patched \
    && ./configure \
    && make libs \
    && make all install
RUN mkdir -p /tmp/OSRA \
    && cd /tmp/OSRA \
    && wget http://downloads.sourceforge.net/project/osra/osra/2.0.1/osra-2.0.1.tgz \
    && tar -xvf /tmp/OSRA/osra-2.0.1.tgz \
    && cd /tmp/OSRA/osra-2.0.1 \
    && ./configure \
    && make all \
    && make install
RUN cd && rm -rf /tmp/OSRA
