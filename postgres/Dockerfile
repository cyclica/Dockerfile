FROM postgres:10
MAINTAINER Steve Constable <steve.constable@cyclicarx.com>
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y locales
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    locale-gen
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
RUN apt-get install -y \
cmake wget build-essential ca-certificates \
    postgresql-server-dev-10 \
    postgresql-client \
    postgresql-plpython-10 \
    postgresql-plpython3-10 \
    python-numpy \
    python-dev \
    sqlite3 \
    libsqlite3-dev \
    libboost-all-dev \
    libboost-dev \
    libboost-system-dev \
    libboost-thread-dev \
    libboost-serialization-dev \
    libboost-python-dev \
    libboost-regex-dev \
    libeigen3-dev
ENV RDBASE=/opt/rdkit
ENV LD_LIBRARY_PATH=$RDBASE/lib:$LD_LIBRARY_PATH
ENV PYTHONPATH=$RDBASE:$PYTHONPATH
RUN wget https://github.com/rdkit/rdkit/archive/Release_2018_09_1.tar.gz -O rdkit.tgz \
    && mkdir $RDBASE \
    && tar xzvf rdkit.tgz -C $RDBASE --strip-components 1 \
    && cd $RDBASE \
    && mkdir build \
    && cd build \
    && cmake -DRDK_BUILD_INCHI_SUPPORT=ON -DPYTHON_EXECUTABLE=/usr/bin/python3 -DPYTHON_INCLUDE_DIR=/usr/include/python3.5m -DPYTHON_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython3.5m.so -DRDK_BUILD_PGSQL=ON -DPostgreSQL_ROOT=/usr/lib/postgresql/10 -DPostgreSQL_TYPE_INCLUDE_DIR=/usr/include/postgresql/10/server .. \
    && make \
    && make install
RUN chmod +x $RDBASE/build/Code/PgSQL/rdkit/pgsql_install.sh && $RDBASE/build/Code/PgSQL/rdkit/pgsql_install.sh

