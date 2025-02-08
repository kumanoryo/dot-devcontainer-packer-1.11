FROM ghcr.io/bearfield/debian-fish:bookworm
#
# set argument
ARG PACKER_VERSION=1.11.*
#
# Add HashiCorp Linux repository and install packer.
USER root
SHELL ["/bin/bash", "-c"]
RUN curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add - \
    && echo "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $(lsb_release -cs) main" > /etc/apt/sources.list.d/hachicorp.list \
    && apt-get update \
    && apt-get install -y \
        packer=$PACKER_VERSION \
    # crean up
    && apt-get autoremove -y \
    && apt-get clean -y \
	&& rm -rf /var/lib/apt/lists/*
#
# set env
ENV DEBIAN_FRONTEND=dialog
LABEL org.opencontainers.image.source https://github.com/bearfield/dot-devcontainer-packer-1.11