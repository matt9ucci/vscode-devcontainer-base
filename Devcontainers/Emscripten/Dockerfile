ARG UBUNTU_VERSION=20.04
FROM ghcr.io/matt9ucci/vscode/ubuntu:$UBUNTU_VERSION

ARG DEBIAN_FRONTEND=noninteractive

RUN set -x \
 && apt-get -qq update \
 && apt-get -qq -o Dpkg::Use-Pty=0 install --no-install-recommends \
	cmake \
	make \
	python3 \
	python-is-python3\
	xz-utils \
 && rm -rf /var/lib/apt/lists/*

ARG USER_NAME=vscode
USER $USER_NAME

# Install emsdk: https://emscripten.org/docs/getting_started/downloads.html
ARG EMSDK=/home/$USER_NAME/emsdk
ARG EMSDK_VERSION=latest
RUN set -ux \
 && git clone --depth 1 https://github.com/emscripten-core/emsdk.git $EMSDK \
 && $EMSDK/emsdk install $EMSDK_VERSION \
 && $EMSDK/emsdk activate $EMSDK_VERSION \
 && echo "source $(realpath $EMSDK/emsdk_env.sh) > /dev/null 2>&1" >> $HOME/.bashrc

# OCI labels: https://github.com/opencontainers/image-spec/blob/main/annotations.md
LABEL \
org.opencontainers.image.authors='Matt Gucci' \
org.opencontainers.image.description='Emsdk and tools for Emscripten development inside VS Code devcontainer.' \
org.opencontainers.image.licenses=MIT \
org.opencontainers.image.title='Emscripten with VSCode'
