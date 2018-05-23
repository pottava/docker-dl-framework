# Keras v2.1 with TensorFlow v1.8
#
# docker run --rm -it pottava/keras ipython
# docker run --rm -it -p 80:8888 pottava/keras

FROM pottava/tensorflow:1.8-note

ENV KERAS_VERSION=2.1.6

RUN pip install --ignore-installed --upgrade "keras == ${KERAS_VERSION}" \
    && find / -depth -type d -name tests -exec rm -rf {} \; \
    && find / -depth -type d -name test -exec rm -rf {} \; \
    && find / -depth -type d -name \__pycache__ -exec rm -rf {} \; \
    && rm -rf /root/.cache
