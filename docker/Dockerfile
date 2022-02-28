FROM pytorch/pytorch:1.10.0-cuda11.3-cudnn8-devel

ENV DEBIAN_FRONTEND=noninteractive
ENV CMAKE_PREFIX_PATH="$(dirname $(which conda))/../"

RUN apt-get update && apt-get install -y git ninja-build libglib2.0-0 libsm6 libxrender-dev libxext6 libgl1-mesa-dev cmake

RUN conda clean --all
RUN conda update -n base -c defaults conda

RUN git clone https://github.com/yuval-alaluf/stylegan3-editing.git /temp
WORKDIR /temp/environment
RUN conda env create -f sg3_env.yaml &&\
	conda init && \
   	echo "conda activate sg3_env" >> ~/.bashrc

#RUN conda activate sg3_env

WORKDIR /workspace
