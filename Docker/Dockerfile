# Sample usage: 
#
# docker build . -t huazhou/ucla_econ_425t_2023w
# docker-compose up
# docker image push huazhou/ucla_econ_425t_2023w
#
# https://github.com/jupyter/docker-stacks
# ubuntu: 22.04 (jammy), R: 4.2.2, Python: 3.10

ARG OWNER=jupyter
ARG BASE_CONTAINER=$OWNER/datascience-notebook
FROM $BASE_CONTAINER 

LABEL maintainer="Hua Zhou <huazhou@ucla.edu>"

# Fix: https://github.com/hadolint/hadolint/wiki/DL4006
# Fix: https://github.com/koalaman/shellcheck/wiki/SC3014
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

USER root

RUN apt-get update --yes && \
    apt-get install --yes --no-install-recommends \
    pandoc \
    pandoc-citeproc \    
    gdebi-core \
    && rm -rf /var/lib/apt/lists/*

# Quarto installation
# Default values can be overridden at build time
# (ARGS are in lower case to distinguish them from ENV)
# Check https://quarto.org/docs/get-started/
# ARG QUARTO_VERSION="0.9.522"
# RUN curl -o quarto-linux-amd64.deb -L https://github.com/quarto-dev/quarto-cli/releases/download/v${QUARTO_VERSION}/quarto-${QUARTO_VERSION}-linux-amd64.deb
RUN curl -LO https://quarto.org/download/latest/quarto-linux-amd64.deb
RUN gdebi --non-interactive quarto-linux-amd64.deb

