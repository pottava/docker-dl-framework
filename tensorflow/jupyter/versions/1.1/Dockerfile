# TensorFlow v1.1 with Jupyter notebook
#
# docker run --rm -it pottava/tensorflow:1.1-note ipython
# docker run --rm -it -p 80:8888 pottava/tensorflow:1.1-note

FROM pottava/tensorflow:1.1

ENV JUPYTER_VERSION=1.0.0

RUN apk --no-cache add tini \

    # Install Jupyter
    && pip install "jupyter == ${JUPYTER_VERSION}" \

    # Clean up
    && find / -type d -name tests -depth -exec rm -rf {} \; \
    && find / -type d -name test -depth -exec rm -rf {} \; \
    && find / -type d -name \__pycache__ -depth -exec rm -rf {} \; \
    && rm -rf /root/.cache

WORKDIR /root/notebook

ENTRYPOINT ["/sbin/tini", "--"]
CMD ["jupyter", "notebook", "--no-browser", "--port=8888", "--ip=0.0.0.0", "--allow-root"]
