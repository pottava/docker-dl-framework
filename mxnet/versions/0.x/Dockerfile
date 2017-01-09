# MXNet v0.8
#
# docker run --rm -it pottava/mxnet:0.8
# docker run --rm pottava/mxnet:0.8 -c 'import mxnet; print(mxnet.__version__)'

FROM pottava/scipy:0.18

ENV MXNET_VERSION=v0.8.0 \
    OPENCV_REPO="http://dl-cdn.alpinelinux.org/alpine/edge/testing"

RUN apk --no-cache add --repository $OPENCV_REPO opencv \
    && apk --no-cache add --repository $OPENCV_REPO opencv-dev \
    && apk --no-cache add --virtual build-deps \
        openblas-dev python3-dev g++ git make \

    # Install MXNet Core without CUDA
    && git clone --branch ${MXNET_VERSION} --depth 1 --recursive \
        https://github.com/dmlc/mxnet/ \
    && cd mxnet \
    && cp make/config.mk . \
    && echo "USE_BLAS=openblas" >>config.mk \
    && make -j$(nproc) \

    # Install MXNet Python package
    && cd python \
    && python setup.py install \

    && apk del --purge -r build-deps \
    && apk del --purge -r opencv-dev \
    && rm -r /root/.cache
