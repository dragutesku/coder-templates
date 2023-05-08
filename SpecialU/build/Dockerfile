# Get latest ubuntu image
FROM ubuntu:latest

# Update and Upgrade Ubuntu
RUN apt-get -y update && apt-get upgrade

# Install necessary packages from ubuntu repos
RUN apt-get install -y \
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

# Install Oh My Zsh
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

ARG USER=coder
RUN useradd --groups sudo --no-create-home --shell /bin/bash ${USER} \
	&& echo "${USER} ALL=(ALL) NOPASSWD:ALL" >/etc/sudoers.d/${USER} \
	&& chmod 0440 /etc/sudoers.d/${USER}
USER ${USER}
WORKDIR /home/${USER}