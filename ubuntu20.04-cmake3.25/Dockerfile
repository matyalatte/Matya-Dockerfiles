# Install Cmake3.25.3 on Ubuntu 20.04
FROM ubuntu:20.04

# Install packages
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
            wget ca-certificates build-essential libssl-dev &&\
    apt-get clean &&\
    rm -rf /var/lib/apt/lists/*

# Installl Cmake
ARG cmake_ver_short="3.25"
ARG cmake_version="${cmake_ver_short}.3"
WORKDIR /root/temp_cmake
RUN wget https://cmake.org/files/v${cmake_ver_short}/cmake-${cmake_version}.tar.gz; \
    tar -xzvf cmake-${cmake_version}.tar.gz
WORKDIR /root/temp_cmake/cmake-${cmake_version}
RUN ./bootstrap; \
    make -j$(nproc); \
    make install
WORKDIR /root
RUN rm -rf temp_cmake

CMD ["/bin/bash"]
