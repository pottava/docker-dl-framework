# MXNet with NVIDIA CUDA 8.0 & cuDNN 5.1
# https://hub.docker.com/r/nvidia/cuda/
#
# docker run --rm pottava/mxnet:0.9-gpu python -c 'import mxnet; print(mxnet.__version__)'
# docker run --rm pottava/mxnet:0.9-gpu nvcc --version
# docker run --rm -it -p 80:8888 pottava/mxnet:0.9-gpu

FROM nvidia/cuda:8.0-cudnn5-devel

ENV MXNET_VERSION=0.9.3 \
    PYTHONPATH=/mxnet/python \
    S6_VERSION=v1.19.1.1 \
    S6_LOGGING=1

RUN BUILD_PACKAGES="build-essential git ca-certificates libopenblas-dev" \
    && apt-get update && apt-get autoremove -y \
    && apt-get install -y $BUILD_PACKAGES \

    # Install MXNet dependencies
    && apt-get install -y libopencv-dev python-numpy python-dev graphviz \

    # Install MXNet
    && git clone --branch v${MXNET_VERSION} --depth 1 --recursive \
        https://github.com/dmlc/mxnet/ \
    && cd mxnet \
    && cp make/config.mk . \
    && echo "USE_CUDA=1" >>config.mk \
    && echo "USE_CUDA_PATH=/usr/local/cuda" >>config.mk \
    && echo "USE_CUDNN=1" >>config.mk \
    && echo "USE_BLAS=openblas" >>config.mk \
    && make -j$(nproc) \

    # Install Python libraries & Jupyter
    && apt-get install -y python-pip python-scipy python-sklearn \
    && pip install jupyter graphviz cython pandas bokeh \

    # Install s6-overlay to execute initialization scripts
    && S6_DL=https://github.com/just-containers/s6-overlay/releases/download \
    && S6_TAR=s6-overlay-amd64.tar.gz \
    && curl --location --silent --show-error -O ${S6_DL}/${S6_VERSION}/${S6_TAR} \
    && tar xzf ${S6_TAR} -C / \
    && echo '#!/usr/bin/execlineb -P' > /etc/cont-init.d/01-link-devnull \
    && echo 'ln /dev/null /dev/raw1394' >> /etc/cont-init.d/01-link-devnull \

    # Clean up
    && find /mxnet -maxdepth 1 -type d -name "[^lp]*" ! -path /mxnet -exec rm -rf {} \; \
    && find /mxnet -maxdepth 1 -type f -name "[^lp]*" -exec rm -rf {} \; \
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && apt-get purge -y --auto-remove $BUILD_PACKAGES \
    && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

WORKDIR /root/notebook

ENTRYPOINT ["/init"]
CMD ["jupyter", "notebook", "--no-browser", "--port=8888", "--ip=0.0.0.0"]
