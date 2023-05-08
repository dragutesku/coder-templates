# Get latest ubuntu image
FROM ubuntu:latest

# Install necessary packages from ubuntu repos
RUN apt-get -y update \
    && apt-get install -y \
    curl \
    get \
    sudo \
    vim \
    git \
    wget \
    zsh \
    ripgrep \
    build-base \
    && rm -rf /var/lib/apt/lists/*

ARG USER=coder
RUN useradd --groups sudo --no-create-home --shell /bin/bash ${USER} \
	&& echo "${USER} ALL=(ALL) NOPASSWD:ALL" >/etc/sudoers.d/${USER} \
	&& chmod 0440 /etc/sudoers.d/${USER}
USER ${USER}
WORKDIR /home/${USER}
