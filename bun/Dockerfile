FROM docker.io/oven/bun:canary-alpine

WORKDIR /app

ENV NODE_ENV production \
    host="0.0.0.0" \
    port="80"

EXPOSE 80

RUN apk add --no-cache curl
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --start-interval=1s --retries=3 CMD curl -fso /dev/null http://localhost/health || exit 1

ARG BUILD_REV
ARG BUILD_DATE
LABEL org.opencontainers.image.title="alwatr/bun" \
      org.opencontainers.image.description="An all-in-one JavaScript runtime & toolkit designed for speed, complete with a bundler, test runner, and Node.js-compatible package manager, packaged by Alwatr." \
      org.opencontainers.image.base.name="docker.io/oven/bun:1.4.0-alpine" \
      org.opencontainers.image.version="1.4.0" \
      org.opencontainers.image.ref.name="1.4.0" \
      org.opencontainers.image.licenses="MIT" \
      org.opencontainers.image.created=${BUILD_DATE} \
      org.opencontainers.image.revision=${BUILD_REV} \
      org.opencontainers.image.vendor="Alwatr" \
      org.opencontainers.image.source="https://github.com/Alwatr/containers/tree/next/bun" \
      org.opencontainers.image.url="https://github.com/Alwatr/containers/tree/next/bun" \
      org.opencontainers.image.documentation="https://github.com/Alwatr/containers/tree/next/bun" \
      org.opencontainers.image.authors="S. Ali Mihandoost <ali.mihandoost@gmail.com> (https://ali.mihandoost.com), S. Amir Mohammad Najafi <njfamirm@gmail.com> (https://njfamirm.ir/)" \
      cloud.alwatr.image.version.full="1.4.0" \
      cloud.alwatr.image.version.short="1"
