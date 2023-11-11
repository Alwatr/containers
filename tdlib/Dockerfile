FROM ghcr.io/alwatr/alpine:3.17.5

ARG TDLIB_VERSION=1.8.0
RUN set -ex; \
    apk add --no-cache --virtual .build-deps \
      curl \
      ca-certificates \
      g++ \
      make \
      cmake \
      gperf \
      libressl-dev \
      zlib-dev \
      zlib-static \
      linux-headers; \
    mkdir /tmp/td/ && cd /tmp/td/; \
    curl -sSLo tdlib.tar.gz https://github.com/tdlib/td/archive/refs/tags/v${TDLIB_VERSION}.tar.gz; \
    tar -xzvf tdlib.tar.gz && cd td-${TDLIB_VERSION}; \
    mkdir build && cd build; \
    cmake -DCMAKE_BUILD_TYPE=Release -DTD_ENABLE_LTO=ON ..; \
    ls -lAhFtr; \
    cmake --build . --target install -j 4; \
    ls -lAhFtr; \
    make install; \
    ls -lAhFtr /usr/local/lib/; \
    apk del .build-deps; \
    rm -rfv /tmp/td/;

ARG BUILD_REV
ARG BUILD_DATE
LABEL org.opencontainers.image.title="alwatr/tdlib" \
      org.opencontainers.image.description="A library to access Telegram database, written in C++ and cross-platform, packaged by Alwatr." \
      org.opencontainers.image.base.name="ghcr.io/alwatr/alpine:3.17" \
      org.opencontainers.image.version="1.8.0" \
      org.opencontainers.image.ref.name="1.8.0" \
      org.opencontainers.image.licenses="MIT" \
      org.opencontainers.image.created=${BUILD_DATE} \
      org.opencontainers.image.revision=${BUILD_REV} \
      org.opencontainers.image.vendor="Alwatr" \
      org.opencontainers.image.source="https://github.com/Alwatr/containers/tree/main/tdlib" \
      org.opencontainers.image.url="https://github.com/Alwatr/containers/tree/main/tdlib" \
      org.opencontainers.image.documentation="https://github.com/Alwatr/containers/tree/main/tdlib" \
      org.opencontainers.image.authors="S. Ali Mihandoost <ali.mihandoost@gmail.com> (https://ali.mihandoost.com), S. Amir Mohammad Najafi <njfamirm@gmail.com> (https://njfamirm.ir/)" \
      cloud.alwatr.image.version.full="1.8.0" \
      cloud.alwatr.image.version.short="1"
