#### 参数：及　线上的权重Ｗ，用变量表示，随机给初始值。

```python
w = tf.Variable(tf.random_normal([2,3], stddev=2, mean=0, seed=1))

# tf.random_normal() : 正态分布
# tf.random_uniform(): 平均分布
# tf.truncated_normal() :去掉过大偏离点的正态分布
# [2,3]: 产生2×3的矩阵
# stddev=2：标准差为2
# mean=0 : 均值为0
# seed=1 : 随机种子

```
```py
# tf.zeros #全0数组 
tf.zeros([3,2],int32) # [[0,0],[0,0],[0,0]]

# tf.ones #全为1数组
tf.ones([3,2],int32)  #[[1,1],[1,1],[1,1]]

# tf.fill #全定值数组
tf.fill([3,2],6)      #[[6,6],[6,6],[6,6]]

# tf.constant 直接给值
tf.constant([3,2,1])  #[3,2,1]

```

#### 神经网络的实现过程：

1. 准备数据集，提取特征，作为输入喂给神经网络（Neural Network, NN）
2. 搭建NN结构，从输入到输出（先搭建计算图，再用会话执行）

        （NN前向传播算法=> 计算输出）
3. 大量特征数据喂给NN,迭代优化NN参数

        （NN反向传播算法=> 优化参数训练模型）
4. 使用训练好的模型预测和分类


#### 前向传播=>搭建模型，实现推理（以全连接网络为例）
eg:生产一批零件将体积x1和重量x2为特征输入NN,通过NN后输出一个数值

+ 变量初始化、计算图节点运算，都要用到会话（with结构）实现
    ```py
    width tf.compat.v1.Session() as sess:
        sess.run()
    ```

+ 变量初始化：在sess.run函数中用`tf.global_variables_initializer()`
    ```py
    init_op = tf.global_variables_initializer()
    sess.run(init_op)
    ```

+ 计算图节点运算：在`sess.run`函数中写入待运算的节点
    ```py
    sess.run(y)
    ```

+ 用`tf.placeholder`站位，在`session.run`函数中用`feed_dict`喂如数据

    ```py
    # 喂如一组数据：
    x = tf.placeholder(tf.float32,shape(1,2))
    sess.run(y.feed_dict={x:[[0.5,0.6]]})

    # 喂如多组数据：
    x = tf.placeholder(tf.float32,shape(None,2))
    sess.run(y,feed_dict={x:[[0.1,0,2],[0.2,0.3],[0.3,0.4],[0.4,0.5]]})
    ```


以下两种方式实现前向传播
 ```py
#coding:utf-8
# 两层简单神经网络（全连接）
import tensorflow as tf

# 定义输入和参数
x = tf.constant([[0.7,0.5]])
w1 = tf.Variable(tf.random_normal([2,3], stddev=1, seed=1))
w2 = tf.Variable(tf.random_normal([3,1], stddev=1, seed=1))

# 定义前向传播过程
a = tf.matmul(x, w1)
y = tf.matmul(a,w2)

# 用会话计算结果
with tf.compat.v1.Session() as sess:
    init_op = tf.global_variables_initializer()
    sess.run(init_op)
    print("y  is :\n",sess.run(y))
# 结果y  is : [[3.0904665]]
 ```

 ```py
 # 定义输入和参数
 # 用placeholder实现输入定义(sess.run中喂入一组数据)

 x = tf.placeholder(tf.float32, shape(1,2))
 w1 = tf.Variable(tf.random_normal([2,3], stddev=1, seed=1))
 w2 = tf.Variable(tf.random_normal([3,1], stddev=1, seed=1))

 # 定义前向传播过程
 a = tf.matmul(x, w1)
 y = tf.matmul(a, w2)

 # 用会话计算结果
 with tf.compat.v1.Session() as sess:
     init_op = tf.global_variables_initializer()
     sess.run(init_op)

     print("y is:",sess.run(y, feed_dict={x: [[0.7,0.5]]}))

# 结果：[[3.0904665]]

```
```py 
 # 两层简单神经网络（全连接）

 import tensorflow as tf

 # 定义输入和参数
 # 用placeholder实现输入定义（sess.run中喂如一组数据）

 x = tf.placeholder(tf.float32, shape = (None,2))
 w1 = tf.Variable(tf.random_normal([2,3], stddev=1, seed=1))
 w2 = tf.Variable(tf.random_normal([3,1], stddev=1, seed=1))

 # 定义前向传播过程
 a = tf.matmul(x, w1)
 y = tf.matmul(a, w2)


 # 用会话计算结果
 with tf.compat.v1.Session() as sess:
     init_op = tf.global_variables_initializer()
     sess.run(init_op)
     print("rusult is : ", sess.run(y, feed_dict=({x: [[0.7,0.5],[0.2,0.3],[0.3,0.4],[0.4,0.5]]})))

     print("w1: ", sess.run(w1))
     print("w2: ", sess.run(w2))
# 结果
#rusult is :  [[3.0904665]
# [1.2236414]
# [1.7270732]
# [2.2305048]]
#w1:  [[-0.8113182   1.4845988   0.06532937]
# [-2.4427042   0.0992484   0.5912243 ]]
#w2:  [[-0.8113182 ]
# [ 1.4845988 ]
# [ 0.06532937]]


```
