# Alwatr Traefik Container

Traefik is designed to work with modern container orchestration platforms like Docker and Kubernetes, and it can automatically discover new services as they are added to the environment. It also provides advanced features like automatic SSL certificate generation and renewal, dynamic routing based on service health checks, and support for multiple backends.

For more information on Traefik, see the official documentation at <https://doc.traefik.io/traefik/>.

## Usage

Check versions from [Alwatr/packages](https://github.com/Alwatr/containers/pkgs/container/traefik)

### Install from the command line

```bash
docker pull ghcr.io/alwatr/traefik:3.0.0-beta4
```

### Use as base image in Dockerfile

```dockerfile
FROM ghcr.io/alwatr/traefik:3.0.0-beta4
```
