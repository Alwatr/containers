FROM docker.io/library/node:20.17.0-alpine3.19

WORKDIR /app
ENV NODE_ENV production

ARG BUILD_REV
ARG BUILD_DATE
LABEL org.opencontainers.image.title="alwatr/node" \
      org.opencontainers.image.description="Cross-platform ECMAScript runtime environment, packaged by Alwatr." \
      org.opencontainers.image.base.name="docker.io/library/node:20.17.0-alpine3.19" \
      org.opencontainers.image.version="20.17.0" \
      org.opencontainers.image.ref.name="20.17.0" \
      org.opencontainers.image.licenses="MIT" \
      org.opencontainers.image.created=${BUILD_DATE} \
      org.opencontainers.image.revision=${BUILD_REV} \
      org.opencontainers.image.vendor="Alwatr" \
      org.opencontainers.image.source="https://github.com/Alwatr/containers/tree/next/node" \
      org.opencontainers.image.url="https://github.com/Alwatr/containers/tree/next/node" \
      org.opencontainers.image.documentation="https://github.com/Alwatr/containers/tree/next/node" \
      org.opencontainers.image.authors="S. Ali Mihandoost <ali.mihandoost@gmail.com> (https://ali.mihandoost.com)" \
      cloud.alwatr.image.version.full="20.17.0" \
      cloud.alwatr.image.version.short="20"
