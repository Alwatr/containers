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
FROM ghcr.io/alwatr/alpine:3.18.4
RUN apk add --no-cache mysql-client
ENTRYPOINT ["mysql"]
```

Only **4s** to build and results in a **41MB** image!

Check versions from [Alwatr/packages](https://github.com/Alwatr/containers/pkgs/container/alpine)

### Install from the command line

```bash
docker pull ghcr.io/alwatr/alpine:3.18.4
```

### Use as base image in Dockerfile

```dockerfile
FROM pull ghcr.io/alwatr/alpine:3.18.4
```
