# TensorFlow v0.12
#
# docker run --rm -it pottava/tensorflow:0.12
# docker run --rm pottava/tensorflow:0.12 -c 'import tensorflow as tf; print(tf.VERSION)'

FROM pottava/miniconda:4.2

ENV TENSORFLOW_VERSION=0.12.1

RUN apk --no-cache add libstdc++ \

    # Install TensorFlow
    && pip install --ignore-installed --upgrade "tensorflow == ${TENSORFLOW_VERSION}" \

    # Clean up
    && find / -type d -name tests -depth -exec rm -rf {} \; \
    && find / -type d -name test -depth -exec rm -rf {} \; \
    && find / -type d -name \__pycache__ -depth -exec rm -rf {} \; \
    && rm -rf /root/.cache

ENTRYPOINT ["python"]
