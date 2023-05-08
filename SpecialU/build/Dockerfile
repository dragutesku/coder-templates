# Download base image ubuntu 22.04
FROM ubuntu

# Disable Prompt During Packages Instalation
ARG DEBIAN_FRONTEND=noninteractive

# Update Ubuntu Software repository
RUN apt update
RUN apt upgrade -y

# Install necessary packages from ubuntu repos
RUN apt install -y curl vim git wget zsh ripgrep build-base

RUN rm -rf /var/lib/apt/lists/*

RUN apt clean

ARG USER=coder
RUN useradd --groups sudo --no-create-home --shell /bin/bash ${USER} \
	&& echo "${USER} ALL=(ALL) NOPASSWD:ALL" >/etc/sudoers.d/${USER} \
	&& chmod 0440 /etc/sudoers.d/${USER}
USER ${USER}
WORKDIR /home/${USER}
