FROM ghcr.io/matt9ucci/vscode/devcontainers/ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive

RUN set -x \
 && apt-get -qq update \
 && apt-get -qq -o Dpkg::Use-Pty=0 install --no-install-recommends \
	build-essential \
	cmake \
	gdb \
	make \
 && rm -rf /var/lib/apt/lists/*

ARG USER_NAME=vscode
USER $USER_NAME

# OCI labels: https://github.com/opencontainers/image-spec/blob/main/annotations.md
LABEL \
org.opencontainers.image.authors='Matt Gucci' \
org.opencontainers.image.description='C/C++ development inside VS Code devcontainer.' \
org.opencontainers.image.licenses=MIT \
org.opencontainers.image.title='C/C++ devcontainer'
