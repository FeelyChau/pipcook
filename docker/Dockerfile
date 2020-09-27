FROM nvidia/cuda:10.1-cudnn7-devel
ARG VER=beta

LABEL version=${VER}
LABEL description="docker image for pipcook runtime"

ENV TF_FORCE_GPU_ALLOW_GROWTH=true

WORKDIR /root/
RUN rm /etc/apt/sources.list.d/nvidia-ml.list /etc/apt/sources.list.d/cuda.list
RUN apt-get update && apt-get install -y curl wget python git
# nvm

RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs

RUN npm install cnpm -g && \
    cnpm install @pipcook/pipcook-cli@${VER} -g && \
    pipcook init ${VER} --tuna -c cnpm
