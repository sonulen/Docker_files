# В качестве базового образа для сборки используем gcc:latest
FROM ubuntu:18.04

MAINTAINER Andrey Tolmachev <sonulen@gmail.com>

# GCC G++ 9
RUN apt-get update && apt-get install -y software-properties-common && \
    add-apt-repository ppa:ubuntu-toolchain-r/test && \
    apt update && apt install -y gcc-9 g++-9 && \
    update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 60 \
    --slave /usr/bin/g++ g++ /usr/bin/g++-9 && \
    update-alternatives --config gcc

# Install git make cmake
RUN apt-get install -y git cmake make

# Install g{test,mock} sources
RUN git clone https://github.com/google/googletest.git && \
    cd googletest && mkdir mybuild && cd mybuild && \
    cmake ../ && \
    make && make install

# Install doxygen for documentation
RUN apt -y install doxygen
