FROM cyclica/django:20181115

MAINTAINER Scott Campbell <scott.campbell@cyclicarx.com>

RUN apt-get update && apt-get install -y curl
RUN curl --silent --location https://deb.nodesource.com/setup_8.x | bash -

RUN apt-get install -y \
    nodejs \
    build-essential \
    python-openbabel

RUN pip install freesasa
