FROM amazonlinux:2023

RUN set -x \
 && yum update \
 && yum -y install \
	bash-completion \
	git \
	gzip \
	jq \
	sudo \
	tar \
	unzip \
	wget \
 && yum clean all

# AWS CLI v2 and bash completion
RUN set -x \
 && curl --silent "https://awscli.amazonaws.com/awscli-exe-linux-$(uname --machine).zip" --output awscliv2.zip \
 && unzip awscliv2.zip \
 && ./aws/install \
 && rm -rf ./aws awscliv2.zip \
 && echo 'complete -C /usr/local/bin/aws_completer aws' >> /etc/bashrc

# Settings for root
RUN set -ux \
 && echo 'complete -C /usr/local/bin/aws_completer aws' >> $HOME/.bashrc

# Settings for vscode: authorized sudo user
ARG USER_NAME=vscode
RUN set -ux \
 && useradd $USER_NAME \
 && echo "$USER_NAME ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$USER_NAME

USER $USER_NAME
