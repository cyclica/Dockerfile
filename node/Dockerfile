FROM cyclica/django:20190103

MAINTAINER Steve Constable <steve.constable@cyclicarx.com>

RUN apt-get update && apt-get install -y curl
RUN curl --silent --location https://deb.nodesource.com/setup_8.x | bash -

RUN apt-get install -y \
    nodejs \
    swig \
    libopenbabel-dev

RUN pip3 install freesasa openbabel
