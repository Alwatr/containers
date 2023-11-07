FROM docker.io/library/alpine:3.17

LABEL org.opencontainers.image.title="alpine"
LABEL org.opencontainers.image.source="https://github.com/Alwatr/containers"
LABEL org.opencontainers.image.description="Minimal Docker image based on Alpine Linux with a complete package index and only 5 MB in size!"
LABEL org.opencontainers.image.authors="Alwatr <hi@alwatr.ir> (https://alwatr.ir)"
LABEL org.opencontainers.image.licenses="MIT"
LABEL org.opencontainers.image.url="https://github.com/Alwatr/containers/alpine"
LABEL org.opencontainers.image.documentation="https://github.com/Alwatr/containers/alpine/README.md"
LABEL org.opencontainers.image.vendor="Alwatr"

ARG APK_TESTING
RUN set -ex; \
  if [ "$APK_TESTING" != "1" ]; then \
    echo "Skip alpine edge testing repository"; \
  else \
    echo "Add alpine edge testing repository"; \
    echo 'https://dl-cdn.alpinelinux.org/alpine/edge/testing/' >> /etc/apk/repositories; \
  fi

ARG APK_INSTALL
RUN set -ex; \
  if [ "$APK_INSTALL" != "1" ]; then \
    echo "Skip apk install"; \
  else \
    echo "Add alpine edge testing repository"; \
    apk add --no-cache ${APK_INSTALL}; \
  fi

CMD ["/bin/sh"]
