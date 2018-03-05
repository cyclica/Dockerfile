FROM cyclica/django:201609

MAINTAINER Scott Campbell <scott.campbell@cyclicarx.com>

RUN apt-get update && apt-get install -y curl
RUN curl --silent --location https://deb.nodesource.com/setup_8.x | bash -

RUN apt-get install -y \
    nodejs \
    build-essential


# Build a docker image from a docker file with this command
# $ docker build -t django-node .

# List all Docker Images
# $ docker images

# Run a docker image as a container
# $ docker run -i -t b9f5a07e1ead /bin/bash
