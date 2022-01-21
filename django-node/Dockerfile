# version: 20220121
FROM cyclica/django:20220121

MAINTAINER Steve Constable <steve.constable@cyclicarx.com>

RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -

RUN apt-get install -y \
    nodejs \
    swig \
    libopenbabel-dev

RUN pip3 install freesasa
