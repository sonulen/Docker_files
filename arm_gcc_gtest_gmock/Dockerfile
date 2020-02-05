# В качестве базового образа для сборки используем gcc:latest
FROM sonulen/gcc_gtest_gmock:latest


# ARM GCC !WITHOUT VERSION
RUN add-apt-repository ppa:team-gcc-arm-embedded/ppa && \
    apt update && apt install -y gcc-arm-embedded
