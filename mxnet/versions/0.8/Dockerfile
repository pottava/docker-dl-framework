# MXNet v0.8
#
# docker run --rm -it pottava/mxnet:0.8
# docker run --rm pottava/mxnet:0.8 python -c 'import mxnet; print(mxnet.__version__)'

FROM ubuntu:14.04

ENV MXNET_VERSION=v0.8.0 \
    PYTHONPATH=/mxnet/python \
    S6_VERSION=v1.18.1.5 \
    S6_LOGGING=1

RUN BUILD_PACKAGES="build-essential git curl" \
    && apt-get update -y && apt-get autoremove -y \
    && apt-get install -y $BUILD_PACKAGES \

    # Install s6-overlay to execute initialization scripts
    && S6_DL=https://github.com/just-containers/s6-overlay/releases/download \
    && S6_TAR=s6-overlay-amd64.tar.gz \
    && curl --location --silent --show-error -O ${S6_DL}/${S6_VERSION}/${S6_TAR} \
    && tar xzf ${S6_TAR} -C / \
    && echo '#!/usr/bin/execlineb -P' > /etc/cont-init.d/01-link-devnull \
    && echo 'ln /dev/null /dev/raw1394' >> /etc/cont-init.d/01-link-devnull \

    # Install necessary packages
    && apt-get install -y libopenblas-dev libopencv-dev python-opencv python-numpy \

    # Install MXNet Core without CUDA
    && git clone --branch ${MXNET_VERSION} --depth 1 --recursive \
        https://github.com/dmlc/mxnet/ \
    && cd mxnet \
    && cp make/config.mk . \
    && echo "USE_BLAS=openblas" >> config.mk \
    && make -j$(nproc) \

    # Clean up
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && apt-get remove --purge -y $BUILD_PACKAGES \
    && rm -rf /var/lib/apt/lists/* ${S6_TAR}

ENTRYPOINT ["/init"]
CMD ["python"]
