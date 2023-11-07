# Alwatr Alpine Container

This is a lightweight Linux image for use in containerized applications. It includes only the necessary packages and dependencies to keep the image size small and efficient, packaged by Alwatr.

## Usage

### Stop doing this

```dockerfile
FROM ubuntu:22.04
RUN apt-get update -q \
  && DEBIAN_FRONTEND=noninteractive apt-get install -qy mysql-client \
  && apt-get clean \
  && rm -rf /var/lib/apt
ENTRYPOINT ["mysql"]
```

This took **28s** to build and yields a **169MB** image!

### Start doing this

```dockerfile
FROM alpine:3.16
RUN apk add --no-cache mysql-client
ENTRYPOINT ["mysql"]
```

Only **4s** to build and results in a **41MB** image!
