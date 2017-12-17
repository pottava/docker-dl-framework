# MXNet v1.0
#
# docker run --rm pottava/mxnet:1.0 python -c 'import mxnet; print(mxnet.__version__)'
# docker run --rm -it pottava/mxnet:1.0 ipython
# docker run --rm -it -p 80:8888 pottava/mxnet:1.0

FROM debian:stretch-slim

ENV MXNET_VERSION=1.0.0 \
    JUPYTER_VERSION=1.0.0

# Install MXNet
RUN apt-get update && apt-get autoremove -y \
    && apt-get install -y python gcc wget graphviz \
    && apt-get install -y libopenblas-dev libopencv-dev python-opencv python-numpy \
    && wget -q https://bootstrap.pypa.io/get-pip.py \
    && python get-pip.py \
    && pip install mxnet==${MXNET_VERSION} \
    && apt-get install -y python-dev \
    && pip install jupyter==${JUPYTER_VERSION} \
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && rm -rf /root/.cache

# Install tini
RUN apt-get install -y gnupg2 \
    && wget -q https://github.com/krallin/tini/releases/download/v0.16.1/tini.asc \
    && wget -q https://github.com/krallin/tini/releases/download/v0.16.1/tini \
    && gpg --keyserver hkp://p80.pool.sks-keyservers.net:80 \
           --recv-keys 595E85A6B1B4779EA4DAAEC70B588DFF0527A9B7 \
    && gpg --verify /tini.asc \
    && rm -rf /tini.asc \
    && chmod +x /tini

WORKDIR /root/notebook

ENTRYPOINT ["/tini", "--"]
CMD ["jupyter", "notebook", "--no-browser", "--port=8888", "--ip=0.0.0.0", "--allow-root"]
