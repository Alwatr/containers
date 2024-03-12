FROM docker.io/library/python:3.12.2-alpine3.18

WORKDIR /app

ARG BUILD_REV
ARG BUILD_DATE
LABEL org.opencontainers.image.title="alwatr/python" \
      org.opencontainers.image.description="Lazy programming language, packaged by Alwatr." \
      org.opencontainers.image.base.name="docker.io/library/python:3.12.0-alpine3.18" \
      org.opencontainers.image.version="3.12.0" \
      org.opencontainers.image.ref.name="3.12.0" \
      org.opencontainers.image.licenses="MIT" \
      org.opencontainers.image.created=${BUILD_DATE} \
      org.opencontainers.image.revision=${BUILD_REV} \
      org.opencontainers.image.vendor="Alwatr" \
      org.opencontainers.image.source="https://github.com/Alwatr/containers/tree/next/python" \
      org.opencontainers.image.url="https://github.com/Alwatr/containers/tree/next/python" \
      org.opencontainers.image.documentation="https://github.com/Alwatr/containers/tree/next/python" \
      org.opencontainers.image.authors="S. Ali Mihandoost <ali.mihandoost@gmail.com> (https://ali.mihandoost.com), S. Amir Mohammad Najafi <njfamirm@gmail.com> (https://njfamirm.ir/)" \
      cloud.alwatr.image.version.full="3.12.0" \
      cloud.alwatr.image.version.short="3"
