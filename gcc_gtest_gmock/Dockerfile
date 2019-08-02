# В качестве базового образа для сборки используем gcc:latest
FROM ubuntu:18.04

MAINTAINER Andrey Tolmachev <sonulen@gmail.com>

# GCC 7.4.0
RUN apt-get update && apt-get install -y software-properties-common && \
    add-apt-repository ppa:ubuntu-toolchain-r/test && \
    apt update && apt install -y gcc-8 g++-8 && \
    update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 60 \
    --slave /usr/bin/g++ g++ /usr/bin/g++-8 && \
    update-alternatives --config gcc

# Install git make cmake
RUN apt-get install -y git cmake make

# Install g{test,mock} sources
RUN git clone https://github.com/google/googletest.git && \
    cd googletest && mkdir mybuild && cd mybuild && \
    cmake ../ && \
    make && make install
