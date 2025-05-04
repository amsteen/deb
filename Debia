# Use Debian base image
FROM debian:bookworm-slim

LABEL maintainer="you@example.com"
LABEL description="Debian image with OpenSSH server"

ENV DEBIAN_FRONTEND=noninteractive

# Install SSH and basic tools
RUN apt-get update && apt-get install -y \
    openssh-server \
    sudo \
    vim \
    curl \
    wget \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Create SSH directory
RUN mkdir /var/run/sshd

# Create a user with password
RUN useradd -m -s /bin/bash dockeruser && \
    echo 'dockeruser:password' | chpasswd && \
    echo 'dockeruser ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

# Expose SSH port
EXPOSE 22

# Start SSH service
CMD ["/usr/sbin/sshd", "-D"]
