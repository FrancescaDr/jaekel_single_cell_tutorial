# Docker images 

Repository for base `Docker` images for code environments. 
The public images can be found on Docker-hub: https://hub.docker.com/repositories/francescadr.

This folder contains the `config` files that were used to create `Docker` images based on [viash](http://viash.io) and the equivalent Dockerfiles.

1. Build with `viash`

`viash build config.vsh.yaml -o target --engine docker --setup build`

2. Build with `Docker`

`docker buildx build --platform <architecture> -t <registry>/<username>/<image-name>:<tag> --push <path-to-dockerfile-directory>`

## Docker repository

- [base_single_cell_analysis](https://hub.docker.com/repository/docker/francescadr/base_single_cell_analysis)
    - Basic environment combining 
    - environment for [scverse GSCN workshops](https://github.com/scverse/202510_workshop_GSCN)

- [base_spatial_analysis](https://hub.docker.com/repository/docker/francescadr/base_spatial_analysis/general)
	- Basic environment combining `pandas: 2.3.3`, `anndata: 0.12.9`, `scanpy: 1.12`, `squidpy: 1.8.0`, `spatialdata: 0.7.1.post1`


## Problem shooting

If you work on a Mac with M1/M2/M3 chip then running viash will upload an image with `OS/ARCH = linux/arm64` which is not compatible with the Linux cluster. To avoid this use the Dockerfile and explicitly define that `linux/amd64` should be used.

Alternatively, you can set that all files should be build using `linux/amd64` with:

```
# Set the default platform
export DOCKER_DEFAULT_PLATFORM=linux/amd64

# Add to your shell profile to make it permanent
echo 'export DOCKER_DEFAULT_PLATFORM=linux/amd64' >> ~/.zshrc
```