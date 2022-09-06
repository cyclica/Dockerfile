# version: 20220411
FROM cyclica/chemnix-lite:20220511

MAINTAINER Steve Constable <steve.constable@cyclicarx.com>

RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -

RUN apt-get install -y \
    nodejs \
    swig \
    libopenbabel-dev \
    postgresql \
    libxml2-dev \
    libxslt1-dev \
    libmysqlclient-dev

RUN pip3 install freesasa
