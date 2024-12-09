FROM nvidia/cuda:11.3.1-devel-ubuntu20.04

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get -qq update && \
    apt-get -qq -y upgrade && \
    apt-get -qq -y --no-install-recommends install \
      build-essential \
      g++ \
      gcc \
      git \
      libgl1-mesa-glx \
      libglib2.0-0 \
      libgtk2.0-dev \
      libopenmpi-dev \
      openmpi-bin \
      openmpi-common \
      wget \
      > /dev/null

# Install miniconda
ENV CONDA_DIR /opt/conda
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh && \
     /bin/bash ~/miniconda.sh -b -p /opt/conda

# Put conda in path so we can use conda activate
ENV PATH=$CONDA_DIR/bin:$PATH
RUN conda install --yes python=3.8 \
      > /dev/null

RUN conda install --yes -c pytorch \
      pytorch==1.10.1 \
      torchvision==0.11.2 \
      torchaudio==0.10.1 \
      cudatoolkit=11.3 \
      > /dev/null

RUN python3 -m pip install --progress-bar off --upgrade pip \
      > /dev/null && \
    python3 -m pip install --progress-bar off \
      Pillow==8.4.0 \
      mmcv-full==1.4.0 \
      mmcv==1.4.0 \
      mmdet==2.20.0 \
      mpi4py==3.0.3 \
      numba==0.48.0 \
      nuscenes-devkit \
      torchpack \
      tqdm \
      > /dev/null

