# Chainer v3.5
# docker run --rm pottava/chainer:3.5 -c 'import chainer; print(chainer.__version__)'

FROM pottava/miniconda:4.2

ENV CHAINER_VERSION=3.5.0

# Install Chainer
RUN apk --no-cache add libstdc++ \
    && pip install setuptools wheel \
    && pip install "chainer == ${CHAINER_VERSION}" \
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && rm -rf /root/.cache

ENTRYPOINT ["python"]
