# MXNet v0.10
#
# docker run --rm pottava/mxnet:0.10 python -c 'import mxnet; print(mxnet.__version__)'
# docker run --rm -it pottava/mxnet:0.10 ipython
# docker run --rm -it -p 80:8888 pottava/mxnet:0.10

FROM debian:jessie-slim

ENV MXNET_VERSION=0.10.0.post2 \
    JUPYTER_VERSION=1.0.0 \
    PYTHONPATH=/mxnet/python \
    S6_VERSION=v1.19.1.1 \
    S6_LOGGING=1

RUN BUILD_PACKAGES="build-essential git curl libopenblas-dev" \
    && apt-get update && apt-get autoremove -y \
    && apt-get install -y $BUILD_PACKAGES python-dev graphviz \

    # Install s6-overlay to execute initialization scripts
    && S6_DL=https://github.com/just-containers/s6-overlay/releases/download \
    && S6_TAR=s6-overlay-amd64.tar.gz \
    && curl --location --silent --show-error -O ${S6_DL}/${S6_VERSION}/${S6_TAR} \
    && tar xzf ${S6_TAR} -C / \
    && echo '#!/usr/bin/execlineb -P' > /etc/cont-init.d/01-link-devnull \
    && echo 'ln /dev/null /dev/raw1394' >> /etc/cont-init.d/01-link-devnull \

    # Install necessary packages
    && apt-get install -y libopencv-dev python-opencv python-numpy \

    # Install MXNet Core without CUDA
    && git clone --branch ${MXNET_VERSION} --depth 1 --recursive \
        https://github.com/apache/incubator-mxnet/ \
    && cd incubator-mxnet \
    && cp make/config.mk . \
    && echo "USE_BLAS=openblas" >> config.mk \
    && make -j$(nproc) \

    # Install Jupyter
    && curl --location --silent --show-error \
        https://bootstrap.pypa.io/get-pip.py | python \
    && pip install "jupyter == ${JUPYTER_VERSION}" \

    # Minimum requirements @see http://mxnet.io/get_started/setup.html
    && pip install graphviz \

    # Clean up
    && find /mxnet -maxdepth 1 -type d -name "[^lp]*" ! -path /mxnet -exec rm -rf {} \; \
    && find /mxnet -maxdepth 1 -type f -name "[^lp]*" -exec rm -rf {} \; \
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && apt-get purge -y --auto-remove $BUILD_PACKAGES \
    && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/* \
        /${S6_TAR} /mxnet/lib/libmxnet.a

WORKDIR /root/notebook

ENTRYPOINT ["/init"]
CMD ["jupyter", "notebook", "--no-browser", "--port=8888", "--ip=0.0.0.0", "--allow-root"]
