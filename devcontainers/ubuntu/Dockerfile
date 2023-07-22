ARG UBUNTU_VERSION=22.04
FROM ubuntu:$UBUNTU_VERSION

ARG DEBIAN_FRONTEND=noninteractive

RUN set -x \
 && apt-get -qq update \
 && apt-get -qq -o Dpkg::Use-Pty=0 upgrade \
 && apt-get -qq -o Dpkg::Use-Pty=0 install --no-install-recommends \
	bash-completion \
	ca-certificates \
	curl \
	git \
	sudo \
	vim \
	wget \
 && rm -rf /var/lib/apt/lists/*

# Settings for root
RUN set -ux \
 && echo '. /etc/bash_completion' >> $HOME/.bashrc

# Settings for vscode: authorized sudo user
ARG USER_NAME=vscode
RUN set -ux \
 && adduser --disabled-login --gecos '' $USER_NAME \
 && adduser $USER_NAME sudo \
 && echo "$USER_NAME ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$USER_NAME \
 && sudo --user $USER_NAME sudo echo 'Test sudo for .sudo_as_admin_successful file'
