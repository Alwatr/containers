# Alwatr Python Container

Lazy programming language, packaged by Alwatr.

## Usage

Check versions from [Alwatr/packages](https://github.com/Alwatr/containers/pkgs/container/python)

### Install from the command line

```bash
docker pull ghcr.io/alwatr/python:3.12.0
```

### Use as base image in Dockerfile

```dockerfile
FROM ghcr.io/alwatr/python:3.12.0

COPY deps.txt ./
RUN pip install --no-cache-dir -r deps.txt

COPY . .

CMD [ "python", "./start.py" ]
```
