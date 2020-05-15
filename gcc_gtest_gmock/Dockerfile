# В качестве базового образа для сборки используем gcc:latest
FROM ubuntu:18.04

MAINTAINER Andrey Tolmachev <sonulen@gmail.com>

# GCC G++ 9
RUN apt-get update && apt-get install -y software-properties-common && \
    add-apt-repository ppa:ubuntu-toolchain-r/test && \
    apt update && apt install -y gcc-9 g++-9 && \
    update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 60 \
    --slave /usr/bin/g++ g++ /usr/bin/g++-9 && \
    update-alternatives --config gcc && \
    apt -y autoremove && apt -y autoclean

# Install git make cmake
RUN apt-get install -y git cmake make && \
    apt -y autoremove && apt -y autoclean

# Install g{test,mock} sources
RUN git clone https://github.com/google/googletest.git && \
    cd googletest && mkdir mybuild && cd mybuild && \
    cmake ../ && \
    make && make install

# Install doxygen for documentation
RUN apt -y install doxygen graphviz && \
    apt -y autoremove && apt -y autoclean

# Install cppcheck && cppcheck-htmlreport
RUN git clone https://github.com/danmar/cppcheck.git && \
    cd cppcheck && \
    mkdir build && \
    cd build && \
    cmake .. && \
    cmake --build . && make install && \
    cd ../ && cp htmlreport/cppcheck-htmlreport /usr/bin/cppcheck-htmlreport && \
    cd ../ && rm -rf cppcheck && \ 
    apt-get -y install python3-pygments && \
    apt -y autoremove && apt -y autoclean
    
# Install clang formatter
RUN apt-get install -y wget && \
    bash -c "$(wget -O - https://apt.llvm.org/llvm.sh)" && \
    apt-get install -y clang-format-10 && \
    ln -s /usr/bin/clang-format-10 /usr/bin/clang-format && \
    apt -y autoremove && apt -y autoclean
   
# Update gcc version after all
RUN update-alternatives --config gcc
