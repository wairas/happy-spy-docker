ARG DOCKER_REGISTRY=public.aml-repo.cms.waikato.ac.nz:443/
FROM ${DOCKER_REGISTRY}debian:bullseye

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get -y install \
          libglib2.0-0 \
          libsm6 \
          libxrender-dev \
          libxext6 \
          python3-setuptools \
          git \
          python3-pip \
          python3-opencv \
          pkg-config \
          gnupg && \
    rm -rf /var/lib/apt/lists/*

# base dependencies
RUN pip install --no-cache-dir -U numpy==1.24.1 && \
    pip install --no-cache-dir matplotlib==3.6.2 && \
    pip install --no-cache-dir Pillow==9.4.0 && \
    pip install --no-cache-dir spectral==0.23.1

# utilities in separate layer, as they will change more often
RUN pip install --no-cache-dir "git+https://github.com/wairas/spy-utilities.git@9797b732d9353d22d88304141494f69e99b47b20"

COPY bash.bashrc /etc/bash.bashrc
