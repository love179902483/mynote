#### 本节目的：搭建第一个神经网络，总结搭建八股

* 基于Tensorflow 的ＮＮ：用张量表示数据，用计算图搭建神经网络，用会话执行计算图，优化线上的权重（参数），得到模型。

* 张量（tensor）：多为数组（列表）
　
　阶：张量的维数

| 维数 | 阶 | 名字         | 例子                       |
|------|----|--------------|----------------------------|
| 0-D  | 0  | 标量 scalar  | s=1111                     |
| 1-D  | 1  | 向量　vector | v=[1,2,3]                  |
| 2-D  | 2  | 矩阵 matrix  | m[[1,2,3],[4,5,6],[7,8,9]] |
| n-D  | n  | 张量 tensor  | t=[[[... n个               |


***张量可以表示０阶到n阶数组（列表）

+ 数据类型：`ft.float32` `tf.int32`

```py
   import tensorflow as tf
  
   a = tf.constant([1.0,2.0])
   b = tf.constant([3.0,4.0])
  
   result = a + b
  
   print(result)

   # 结果: Tensor("add:0", shape=(2,), dtype=float32)
   # add: 0  //节点名:第一个输出
   # shape=(2,) //维度：第一维数组长度为２
   # dtype=float32  //数据类型
```


+ 计算图（Graph）：搭建神经网络的过程，只搭建，不运算;
+ 会话（session）: 执行计算图中的节点运算；   
```python
  import tensorflow as tf

  x = tf.constant([[1.0,2.0]])
  w = tf.constant([[3.0],[4.0]])
  
  y = tf.matmul(x,w)
  
  print(y)
 
  with tf.compat.v1.Session() as sess:
      print(sess.run(y))

  # 结果：Tensor("MatMul:0", shape=(1, 1), dtype=float32)
  # [[11.]]
```


