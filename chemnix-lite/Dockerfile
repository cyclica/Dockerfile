# version: 20230621
FROM ubuntu:22.04
MAINTAINER Steve Constable <steve.constable@cyclicarx.com>
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y locales
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    locale-gen
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
RUN apt-get install -y \
    dssp \
    git \
    libboost-filesystem-dev \
    libboost-program-options-dev \
    libboost-python-dev \
    libboost-thread-dev \
    libcurl4-nss-dev \
    libffi-dev \
    libpango-1.0.0 \
    libpangoft2-1.0.0 \
    libpq-dev \
    openbabel \
    openjdk-11-jre-headless \
    python3-brotli \
    python3-cffi \
    python3-pip \
    swig \
    wget
RUN wget -c https://github.com/rdk/p2rank/releases/download/2.4/p2rank_2.4.tar.gz -P ./p2rank && \
    tar zxf ./p2rank/p2rank_2.4.tar.gz  -C ./p2rank/
ENV PATH "$PWD/p2rank/p2rank_2.4:$PATH"
