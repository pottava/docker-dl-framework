# MXNet v1.0 with Jupyter notebook
#
# docker run --rm -it pottava/mxnet:1.0 ipython
# docker run --rm -it -p 80:8888 pottava/mxnet:1.0

FROM pottava/mxnet:1.0

ENV JUPYTER_VERSION=1.0.0

# Install Jupyter
RUN apt-get update && apt-get autoremove -y \
    && apt-get install -y python-dev \
    && pip install jupyter==${JUPYTER_VERSION} \
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && rm -rf /root/.cache

# Install tini
RUN wget -q https://github.com/krallin/tini/releases/download/v0.16.1/tini \
    && chmod +x /tini

WORKDIR /root/notebook

ENTRYPOINT ["/tini", "--"]
CMD ["jupyter", "notebook", "--no-browser", "--port=8888", "--ip=0.0.0.0", "--allow-root"]
