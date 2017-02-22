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
・0.9-notebook ([mxnet/jupyter/versions/1.0/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/mxnet/jupyter/versions/1.0/Dockerfile))  
・0.8 ([mxnet/versions/0.8/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/mxnet/versions/0.8/Dockerfile))  

### Usage

Using the Python default interpreter:

```
$ docker run --rm -it pottava/mxnet
Python 2.7.6 (default, Oct 26 2016, 20:30:19)
[GCC 4.8.4] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> import mxnet
>>> print(mxnet.__version__)
0.8.0
```

With iPython:

```
$ docker run --rm -it pottava/mxnet:0.9-notebook ipython
```

With Jupyter notebook:

```
$ docker run --rm -it -p 80:8888 pottava/mxnet:0.9-notebook
```


## TensorFlow

### Images

https://hub.docker.com/r/pottava/tensorflow/

### Available Tags

https://hub.docker.com/r/pottava/tensorflow/tags/

### Supported tags and respective `Dockerfile` links

・latest ([tensorflow/versions/1.0/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/versions/1.0/Dockerfile))  
・note ([tensorflow/jupyter/versions/1.0/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/jupyter/versions/1.0/Dockerfile))  
・1.0 ([tensorflow/versions/1.0/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/versions/1.0/Dockerfile))  
・1.0-note ([tensorflow/jupyter/versions/1.0/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/jupyter/versions/1.0/Dockerfile))  
・0.12 ([tensorflow/versions/0.x/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/versions/0.x/Dockerfile))  

### Usage

Using the Python default interpreter:

```
$ docker run --rm -it pottava/tensorflow
Python 3.5.2 (default, Dec 22 2016, 10:15:38)
[GCC 6.2.1 20160822] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> import tensorflow
>>> print(tensorflow.__version__)
1.0.0
```

With iPython:

```
$ docker run --rm -it pottava/tensorflow:note ipython
```

With Jupyter notebook:

```
$ docker run --rm -it -p 80:8888 pottava/tensorflow:note
```
