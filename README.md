DeepLearning frameworks
---

## TensorFlow

### Images

https://hub.docker.com/r/pottava/tensorflow/

### Available Tags

https://hub.docker.com/r/pottava/tensorflow/tags/

### Supported tags and respective `Dockerfile` links

・latest ([tensorflow/versions/0.x/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/versions/0.12/Dockerfile))  
・0.12 ([tensorflow/versions/0.x/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/versions/0.12/Dockerfile))  
・0.12-notebook ([tensorflow/jupyter/versions/0.x/Dockerfile](https://github.com/pottava/docker-dl-framework/blob/master/tensorflow/jupyter/versions/1.0/Dockerfile))  

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
0.12.1
```

With iPython:

```
$ docker run --rm -it pottava/tensorflow:0.12-notebook ipython
```

With Jupyter notebook:

```
$ docker run --rm -it -p 80:8888 pottava/tensorflow:0.12-notebook
```
