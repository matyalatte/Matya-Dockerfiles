# Install Cmake3.25.3 on Alpine Linux 3.16.5
FROM alpine:3.16.5

# Install packages
RUN apk update && \
    apk add --no-cache \
        musl-dev make gcc g++ file alpine-sdk linux-headers wget openssl-dev

# Install Cmake
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

CMD ["/bin/sh"]
