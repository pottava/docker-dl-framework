# TensorFlow v1.3
#
# docker run --rm -it pottava/tensorflow:1.3
# docker run --rm pottava/tensorflow:1.3 -c 'import tensorflow as tf; print(tf.VERSION)'

FROM pottava/miniconda:4.3

ENV TENSORFLOW_VERSION=1.3.0

RUN apk --no-cache add libstdc++ \
    && pip install wheel \

    # Install TensorFlow
    && pip install --ignore-installed --upgrade "tensorflow == ${TENSORFLOW_VERSION}" \

    # Clean up
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && rm -rf /root/.cache

ENTRYPOINT ["python"]
