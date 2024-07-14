# Use Ubuntu 22.04 LTS as the base image
FROM python:3.12 AS base

# Label the image
LABEL maintainer="James Joseph <james.joseph@aspentech.com>"
LABEL version="1.0"
LABEL description="This is a devcontainer image for python3 development for Control System"

# Set non-interactive frontend (avoid tzdata prompt)
ARG DEBIAN_FRONTEND=noninteractive

# Update and install dependencies
RUN apt-get update && \
    apt-get install -y \
    libblas-dev \
    liblapack-dev \
    wget \
    sudo \
    gcc \
    gfortran \
    cmake \
    ninja-build \
    git \
    tree \
    zsh \
    fonts-powerline

# Set root password
RUN echo "root:your_root_password_here" | chpasswd

# Install Packages using pip for Python 3.11
RUN pip3 install --no-cache-dir slycot control harold jupyterlab

# Create user vscode, add to sudo group, set default shell to zsh, and set password
RUN useradd -m -G sudo vscode && \
    echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/vscode && \
    echo "vscode:vscode" | chpasswd

# Install Oh My Zsh
RUN wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O /home/vscode/install.sh && \
    chown vscode:vscode /home/vscode/install.sh && \
    su - vscode -c "sh /home/vscode/install.sh --unattended" && \
    rm /home/vscode/install.sh

# Install Powerline fonts
RUN su - vscode -c "git clone https://github.com/powerline/fonts.git --depth=1" && \
    su - vscode -c "cd fonts && ./install.sh && cd .. && rm -rf fonts"

# Set Zsh theme to arrow
RUN su - vscode -c "sed -i 's/ZSH_THEME=\".*\"/ZSH_THEME=\"arrow\"/' ~/.zshrc" 

# Ensure vscode user owns home and workspace directories
RUN chown -R vscode:vscode /home/vscode

# Set the default shell to zsh for vscode user
RUN chsh -s /usr/bin/zsh vscode

# Switch to vscode user
USER vscode

# Set working directory
WORKDIR /home/vscode

# Clean up
RUN sudo apt-get clean && \
    sudo rm -rf /var/lib/apt/lists/*

# Expose JupyterLab port
EXPOSE 8888
