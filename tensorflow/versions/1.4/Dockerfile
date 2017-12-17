# TensorFlow v1.4
#
# docker run --rm -it pottava/tensorflow:1.4
# docker run --rm pottava/tensorflow:1.4 -c 'import tensorflow as tf; print(tf.VERSION)'

FROM pottava/miniconda:4.2

ENV TENSORFLOW_VERSION=1.4.1

RUN apk --no-cache add libstdc++ \
    && pip install setuptools wheel \
    && pip install --ignore-installed --upgrade "tensorflow == ${TENSORFLOW_VERSION}" \
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && rm -rf /root/.cache

ENTRYPOINT ["python"]
