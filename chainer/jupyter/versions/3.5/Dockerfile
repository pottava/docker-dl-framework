# Chainer v3.5 with Jupyter notebook
#
# docker run --rm -it pottava/chainer:3.5-note ipython
# docker run --rm -it -p 80:8888 pottava/chainer:3.5-note

FROM pottava/chainer:3.5

ENV JUPYTER_VERSION=1.0.0

RUN apk --no-cache add tini \
    && pip install "jupyter == ${JUPYTER_VERSION}" \
    && pip install backcall \
    && conda install -y -c conda-forge jupyter_contrib_nbextensions \
    && find / -type d -name tests -depth -exec rm -rf {} \; \
    && find / -type d -name test -depth -exec rm -rf {} \; \
    && find / -type d -name \__pycache__ -depth -exec rm -rf {} \; \
    && rm -rf /root/.cache

WORKDIR /root/notebook
ADD jupyter_notebook_config.py /root/.jupyter/

ENTRYPOINT ["/sbin/tini", "--"]
CMD ["jupyter", "notebook"]
