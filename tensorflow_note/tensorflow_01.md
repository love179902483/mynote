#### 这些教程是针对tensorflow的教程，主要是为了手写数字的识别

1. 安装tensorflow：
　
> pip install tensorflow

> pip install tensorflow-gpu

注：　安装完成tensorflow之后如果numpy的版本过高会爆提示:

```py
        /usr/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:516: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          _np_qint8 = np.dtype([("qint8", np.int8, 1)])
        /usr/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:517: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          _np_quint8 = np.dtype([("quint8", np.uint8, 1)])
        /usr/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:518: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          _np_qint16 = np.dtype([("qint16", np.int16, 1)])
        /usr/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:519: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          _np_quint16 = np.dtype([("quint16", np.uint16, 1)])
        /usr/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:520: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          _np_qint32 = np.dtype([("qint32", np.int32, 1)])
        /usr/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:525: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          np_resource = np.dtype([("resource", np.ubyte, 1)])
        /usr/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:541: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          _np_qint8 = np.dtype([("qint8", np.int8, 1)])
        /usr/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:542: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          _np_quint8 = np.dtype([("quint8", np.uint8, 1)])
        /usr/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:543: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          _np_qint16 = np.dtype([("qint16", np.int16, 1)])
        /usr/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:544: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          _np_quint16 = np.dtype([("quint16", np.uint16, 1)])
        /usr/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:545: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          _np_qint32 = np.dtype([("qint32", np.int32, 1)])
        /usr/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:550: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
          np_resource = np.dtype([("resource", np.ubyte, 1)])
```


这里先查看numpy的版本 `pip3 show numpy`:

```
        Name: numpy
        Version: 1.16.0
        Summary: NumPy is the fundamental package for array computing with Python.
        Home-page: https://www.numpy.org
        Author: Travis E. Oliphant et al.
        Author-email: None
        License: BSD
        Location: /usr/lib/python3.7/site-packages
        Requires:
        Required-by: tensorflow, tensorflow-gpu, tensorboard, opencv-python, matplotlib, Keras-Preprocessing, Keras-Applications, h5pvy
```
