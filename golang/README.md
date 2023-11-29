# Alwatr Golang Container

Go (golang) is a general purpose, higher-level, imperative programming language, packaged by Alwatr.

## Usage

Check versions from [Alwatr/packages](https://github.com/Alwatr/containers/pkgs/container/golang)

### Install from the command line

```bash
docker pull ghcr.io/alwatr/golang:1.21.4
```

### Use as base image in Dockerfile

```dockerfile
FROM ghcr.io/alwatr/golang:1.21.4

WORKDIR /usr/src/app

# Pre-copy/cache go.mod to pre-download dependencies and only re-download them in subsequent builds if they change.
COPY go.mod go.sum ./
RUN go mod download && go mod verify

COPY . .
RUN go build -v -o /usr/local/bin/my-app ./

CMD ["my-app"]
```

### Use as a builder image in a multi-stage Dockerfile

```dockerfile
FROM ghcr.io/alwatr/golang:1.21.4 AS builder

WORKDIR /usr/src/app

# Pre-copy/cache go.mod to pre-download dependencies and only re-download them in subsequent builds if they change.
COPY go.mod go.sum ./
RUN go mod download && go mod verify

COPY . .
RUN go build -v -o /usr/local/bin/my-app ./

FROM ghcr.io/alwatr/alpine:3.18

COPY --from=builder /usr/local/bin/my-app /usr/local/bin/my-app

CMD ["my-app"]
```
