# Keras v2.0 with TensorFlow v1.3
#
# docker run --rm -it pottava/keras ipython
# docker run --rm -it -p 80:8888 pottava/keras

FROM pottava/tensorflow:1.3-note

ENV KERAS_VERSION=2.0.8

RUN pip install wheel \

    # Install Keras
    && pip install --ignore-installed --upgrade "keras == ${KERAS_VERSION}" \

    # Clean up
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && rm -rf /root/.cache
