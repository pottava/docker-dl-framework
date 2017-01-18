# MXNet v0.8 with Jupyter notebook
#
# docker run --rm -it pottava/mxnet:0.8-notebook ipython
# docker run --rm -it -p 80:8888 pottava/mxnet:0.8-notebook

FROM pottava/mxnet:0.8

ENV JUPYTER_VERSION=1.0.0

RUN apt-get update -y && apt-get autoremove -y \
    && apt-get install -y build-essential git curl wget \
        python-pip python-dev graphviz \

    # Install Jupyter
    && pip install "jupyter == ${JUPYTER_VERSION}" \

    # Minimum requirements @see http://mxnet.io/get_started/setup.html
    && pip install graphviz \

    # Clean up
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /root/notebook

CMD ["jupyter", "notebook", "--no-browser", "--port=8888", "--ip=0.0.0.0"]
