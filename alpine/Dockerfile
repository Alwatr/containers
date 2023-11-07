FROM docker.io/library/alpine:3.17

ARG BUILD_REV
ARG BUILD_DATE
LABEL org.opencontainers.image.title="alwatr/alpine" \
      org.opencontainers.image.description="This is a lightweight Linux image for use in containerized applications. It includes only the necessary packages and dependencies to keep the image size small and efficient, packaged by Alwatr." \
      org.opencontainers.image.base.name="docker.io/library/alpine:3.17" \
      org.opencontainers.image.version="3.17" \
      org.opencontainers.image.ref.name="3.17" \
      org.opencontainers.image.licenses="MIT" \
      org.opencontainers.image.created=${BUILD_DATE} \
      org.opencontainers.image.revision=${BUILD_REV} \
      org.opencontainers.image.vendor="Alwatr" \
      org.opencontainers.image.source="https://github.com/Alwatr/containers/tree/main/alpine" \
      org.opencontainers.image.url="https://github.com/Alwatr/containers/tree/main/alpine" \
      org.opencontainers.image.documentation="https://github.com/Alwatr/containers/tree/main/alpine" \
      org.opencontainers.image.authors="S. Ali Mihandoost <ali.mihandoost@gmail.com> (https://ali.mihandoost.com), S. Amir Mohammad Najafi <njfamirm@gmail.com> (https://njfamirm.ir/)"


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
