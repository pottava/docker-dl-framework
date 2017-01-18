# MXNet v0.8 with Jupyter notebook
#
# docker run --rm -it pottava/mxnet:0.8-notebook ipython
# docker run --rm -it -p 80:8888 pottava/mxnet:0.8-notebook

FROM pottava/mxnet:0.8

ENV JUPYTER_VERSION=1.0.0

RUN BUILD_PACKAGES="build-essential python-pip python-dev" \
    && apt-get update -y && apt-get autoremove -y \
    && apt-get install -y $BUILD_PACKAGES \

    # Install Jupyter
    && pip install "jupyter == ${JUPYTER_VERSION}" \

    # Clean up
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && apt-get remove --purge -y $BUILD_PACKAGES \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /root/notebook

CMD ["jupyter", "notebook", "--no-browser", "--port=8888", "--ip=0.0.0.0"]
