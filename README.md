# Go (Golang) Docker Images - Bullseye Only

This repository contains Dockerfiles for building Go (Golang) Docker images based on Debian Bullseye.

## Overview

This is a simplified fork of the [docker-library/golang](https://github.com/docker-library/golang) repository, customized to:
- Generate only Debian Bullseye-based images
- Support publishing to custom registries via GitHub Actions
- Maintain a streamlined codebase focused on a single variant

## Features

- **Single Variant**: Only generates Bullseye-based images (no Alpine, Windows, or other Debian versions)
- **Custom Registry Publishing**: Built-in GitHub Actions workflow for publishing to your own registry
- **Automated Updates**: Scripts to automatically update Go versions from upstream
- **Multi-Architecture Support**: Supports all architectures that Go provides binaries for

## Usage

### Updating Go Versions and Generating Dockerfiles

```bash
# Update versions.json from upstream and generate all Dockerfiles
./update.sh

# Update and generate for specific version(s)
./update.sh 1.25
./update.sh 1.24 1.25
```

### Testing Images Locally

```bash
# Test all versions locally
./test-local.sh

# Test specific version
./test-local.sh 1.25
./test-local.sh 1.24 1.25
```

This script builds the images locally and runs the same tests as the CI workflow (go version, go env, compilation, etc.) without pushing to any registry.

### Publishing Images

Configure GitHub Secrets:
- `DOCKER_REGISTRY_URL` - Your registry URL (e.g., `ghcr.io`, `registry.example.com`, `docker.io`)
- `DOCKER_REGISTRY_USERNAME` - Registry username
- `DOCKER_REGISTRY_PASSWORD` - Registry password/token

Images will be automatically built, tested, and published on push to `master` branch or when tags are pushed.

Images will be automatically published on push to `main`/`master` branches, or manually via workflow dispatch.

## Attribution

This repository is based on the work from [docker-library/golang](https://github.com/docker-library/golang), which is maintained by the Docker Community. The original repository is part of the [Docker Official Images](https://github.com/docker-library/official-images) program.

Significant modifications:
- Removed support for Alpine, Windows, and other Debian variants
- Added custom registry publishing functionality
- Simplified codebase to support only Bullseye variant

## License

See [LICENSE](LICENSE) file for details.
