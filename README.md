DeepLearning frameworks
---

## MXNet

### Images

https://hub.docker.com/r/pottava/mxnet/

### Available Tags

https://hub.docker.com/r/pottava/mxnet/tags/

### Supported tags and respective `Dockerfile` links

・latest ([mxnet/versions/0.9/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/mxnet/versions/0.9/Dockerfile))  
・0.9 ([mxnet/versions/0.9/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/mxnet/versions/0.9/Dockerfile))  
・0.8 ([mxnet/versions/0.8/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/mxnet/versions/0.8/Dockerfile))  

### Usage

Using the Python default interpreter:

```
$ docker run --rm -it pottava/mxnet python
Python 2.7.9 (default, Jun 29 2016, 13:08:31)
[GCC 4.9.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> import mxnet
>>> print(mxnet.__version__)
0.9.3
```

With iPython:

```
$ docker run --rm -it pottava/mxnet ipython
```

With Jupyter notebook:

```
$ docker run --rm -it -p 80:8888 pottava/mxnet
```


## TensorFlow

### Images

https://hub.docker.com/r/pottava/tensorflow/

### Available Tags

https://hub.docker.com/r/pottava/tensorflow/tags/

### Supported tags and respective `Dockerfile` links

・latest ([tensorflow/versions/1.1/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/versions/1.1/Dockerfile))  
・note ([tensorflow/jupyter/versions/1.1/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/jupyter/versions/1.1/Dockerfile))  
・1.1 ([tensorflow/versions/1.1/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/versions/1.1/Dockerfile))  
・1.1-note ([tensorflow/jupyter/versions/1.1/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/jupyter/versions/1.1/Dockerfile))  

### Usage

Using the Python default interpreter:

```
$ docker run --rm -it pottava/tensorflow
Python 3.6.0 |Continuum Analytics, Inc.| (default, Dec 23 2016, 12:22:00)
[GCC 4.4.7 20120313 (Red Hat 4.4.7-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> import tensorflow
>>> print(tensorflow.__version__)
1.1.0
```

With iPython:

```
$ docker run --rm -it pottava/tensorflow:note ipython
```

With Jupyter notebook:

```
$ docker run --rm -it -p 80:8888 pottava/tensorflow:note
```


## Keras with TensorFlow backend

### Supported tags and respective `Dockerfile` links

・latest ([tensorflow/keras/versions/2.0/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/keras/versions/2.0/Dockerfile))  
・2.0 ([tensorflow/keras/versions/2.0/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/keras/versions/2.0/Dockerfile))  

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
