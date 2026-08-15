FROM docker.io/library/node:24.19.0-alpine

WORKDIR /app

ENV NODE_ENV production \
    host="0.0.0.0" \
    port="80"

EXPOSE 80

RUN apk add --no-cache curl
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --start-interval=1s --retries=3 CMD curl -fso /dev/null http://localhost/health || exit 1

ARG BUILD_REV
ARG BUILD_DATE
LABEL org.opencontainers.image.title="alwatr/node" \
      org.opencontainers.image.description="Cross-platform ECMAScript runtime environment, packaged by Alwatr." \
      org.opencontainers.image.base.name="docker.io/library/node:24.19.0-alpine" \
      org.opencontainers.image.version="24.19.0" \
      org.opencontainers.image.ref.name="24.19.0" \
      org.opencontainers.image.licenses="MIT" \
      org.opencontainers.image.created=${BUILD_DATE} \
      org.opencontainers.image.revision=${BUILD_REV} \
      org.opencontainers.image.vendor="Alwatr" \
      org.opencontainers.image.source="https://github.com/Alwatr/containers/tree/next/node" \
      org.opencontainers.image.url="https://github.com/Alwatr/containers/tree/next/node" \
      org.opencontainers.image.documentation="https://github.com/Alwatr/containers/tree/next/node" \
      org.opencontainers.image.authors="S. Ali Mihandoost <ali.mihandoost@gmail.com> (https://ali.mihandoost.com)" \
      cloud.alwatr.image.version.full="24.19.0" \
      cloud.alwatr.image.version.short="24"
