DeepLearning frameworks
---

## MXNet

### Images

https://hub.docker.com/r/pottava/mxnet/

### Available Tags

https://hub.docker.com/r/pottava/mxnet/tags/

### Supported tags and respective `Dockerfile` links

・latest ([mxnet/versions/1.0/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/mxnet/versions/1.0/Dockerfile))  
・1.0 ([mxnet/versions/1.0/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/mxnet/versions/1.0/Dockerfile))  
・1.0-note ([mxnet/versions/1.0/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/mxnet/jupyter/versions/1.0/Dockerfile))  

### Usage

Using the Python default interpreter:

```
$ docker run --rm -it pottava/mxnet:1.0
Python 2.7.13 (default, Nov 24 2017, 17:33:09)
[GCC 6.3.0 20170516] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> import mxnet
>>> print(mxnet.__version__)
1.0.0
```

With iPython:

```
$ docker run --rm -it pottava/mxnet:1.0-note ipython
```

With Jupyter notebook:

```
$ docker run --rm -it -p 80:8888 pottava/mxnet:1.0-note
```


## TensorFlow

### Images

https://hub.docker.com/r/pottava/tensorflow/

### Available Tags

https://hub.docker.com/r/pottava/tensorflow/tags/

### Supported tags and respective `Dockerfile` links

・latest ([tensorflow/versions/1.4/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/versions/1.4/Dockerfile))  
・1.4 ([tensorflow/versions/1.4/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/versions/1.4/Dockerfile))  
・1.4-note ([tensorflow/jupyter/versions/1.4/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/jupyter/versions/1.4/Dockerfile))  

### Usage

Using the Python default interpreter:

```
$ docker run --rm -it pottava/tensorflow:1.4
Python 3.5.2 |Continuum Analytics, Inc.| (default, Jul  2 2016, 17:53:06)
[GCC 4.4.7 20120313 (Red Hat 4.4.7-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> import tensorflow
>>> print(tensorflow.__version__)
1.4.1
```

With iPython:

```
$ docker run --rm -it pottava/tensorflow:note ipython
```

With Jupyter notebook:

```
$ docker run --rm -it -p 80:8888 pottava/tensorflow:note
```


## Keras

### Supported tags and respective `Dockerfile` links

・latest ([tensorflow/keras/versions/2.1/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/keras/versions/2.1/Dockerfile))  
・2.1 ([tensorflow/keras/versions/2.1/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/keras/versions/2.1/Dockerfile))  
・2.1-tensorflow1.4 ([tensorflow/keras/versions/2.1-tf1.4/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/keras/versions/2.1-tf1.4/Dockerfile))  

### Usage

```
$ docker run --rm -it pottava/keras ipython
Python 3.6.0 |Continuum Analytics, Inc.| (default, Dec 23 2016, 12:22:00)
Type 'copyright', 'credits' or 'license' for more information
IPython 6.0.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: import tensorflow
In [2]: print(tensorflow.__version__)
1.1.0
```

With Jupyter notebook:

```
$ docker run --rm -it -p 80:8888 pottava/keras
```
