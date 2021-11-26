FROM postgres:12
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
    postgresql-server-dev-12 \
    postgresql-client-12 \
    postgresql-plpython3-12 \
    python3-dev \
    python3-numpy \
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
RUN wget https://github.com/rdkit/rdkit/archive/Release_2020_03_4.tar.gz -O rdkit.tgz \
    && mkdir $RDBASE \
    && tar xzvf rdkit.tgz -C $RDBASE --strip-components 1 \
    && cd $RDBASE \
    && mkdir build \
    && cd build \
    && cmake -DRDK_BUILD_INCHI_SUPPORT=ON -DBoost_INCLUDE_DIR=/usr/include -DBoost_DIR=/usr/lib/x86_64-linux-gnu -DBoost_NO_BOOST_CMAKE=TRUE -DPYTHON_EXECUTABLE=/usr/bin/python3 -DPYTHON_INCLUDE_DIR=/usr/include/python3.9 -DPYTHON_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython3.9.so -DRDK_BUILD_PGSQL=ON -DPostgreSQL_ROOT=/usr/lib/postgresql/12 -DPostgreSQL_TYPE_INCLUDE_DIR=/usr/include/postgresql/12/server .. \
    && make \
    && make install
RUN chmod +x $RDBASE/build/Code/PgSQL/rdkit/pgsql_install.sh && $RDBASE/build/Code/PgSQL/rdkit/pgsql_install.sh

