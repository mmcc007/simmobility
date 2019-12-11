FROM ubuntu:18.04

RUN apt-get update
RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata
RUN apt-get install -y \
         libboost-all-dev \
         libtinyxml-dev \
         libpq-dev \
         libxerces-c-dev \
         libjsoncpp-dev \
         xsdcxx \
         liblua5.2-dev \
         g++ \
         git \
         qgit \
         cmake \
         libcppunit-dev \
         doxygen \
         libglpk-dev \
         libssl-dev \
         libsoci-dev \
         postgresql \
         binutils \
         libproj-dev \
         gdal-bin \
         python \
         python-pip \
         libssl-dev \
         python-pandas \
         python-matplotlib \
         python-numpy \
         python-crypto \
         python-psycopg2

RUN git clone https://github.com/smart-fm/simmobility-prod.git

RUN cmake --version

RUN cd simmobility-prod/dev/Basic && \
    mkdir Debug && \
    cd Debug && \
    cmake -DBUILD_SHORT="ON" -DBUILD_MEDIUM="ON" -DBUILD_LONG="ON" ..

RUN sed -i '/#include <boost\/thread.hpp>/a #include <iostream>' simmobility-prod/dev/Basic/short/entities/fmodController/FMOD_Client.cpp

RUN cd simmobility-prod/dev/Basic/Debug && \
    make