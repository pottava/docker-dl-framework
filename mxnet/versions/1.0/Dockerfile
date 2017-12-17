# MXNet v1.0
# docker run --rm pottava/mxnet:1.0 python -c 'import mxnet; print(mxnet.__version__)'

FROM debian:stretch-slim

ENV MXNET_VERSION=1.0.0

# Install MXNet
RUN apt-get update && apt-get autoremove -y \
    && apt-get install -y python gcc wget graphviz \
    && apt-get install -y libopenblas-dev libopencv-dev python-opencv python-numpy \
    && wget -q https://bootstrap.pypa.io/get-pip.py \
    && python get-pip.py \
    && pip install mxnet==${MXNET_VERSION} \
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && find / -depth -type d -name '*.egg-info' -exec rm -rf {} \; \
    && rm -rf /root/.cache

ENTRYPOINT ["python"]
