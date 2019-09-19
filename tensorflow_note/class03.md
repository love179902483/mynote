#### 反向传播=>训练模型参数，在所有三叔上用梯度下降，使用NN模型在训练数据上的损失函数最小

+ 损失函数(loss): 预测值(y)与已知答案(y_)的差距

+ 均方误差MSE : <a href="https://www.codecogs.com/eqnedit.php?latex=MSE(y_,y)=\frac{\sum_{i=1}^{n}&space;(y-y_)^{2}}{n}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?MSE(y_,y)=\frac{\sum_{i=1}^{n}&space;(y-y_)^{2}}{n}" title="MSE(y_,y)=\frac{\sum_{i=1}^{n} (y-y_)^{2}}{n}" /></a>

   loss = tf.reduce_mean(tf.square(y_-y))

+ 反向传播训练方法：以减少loss值为优化目标：
    ```
    train_step = tf.train.GradientDescentOptimizer(learning_rate).minimize(loss)
    train_step = tf.train.MomentumOptimizer(learning_rate,momentum).minimize(loss)
    train_step = tf.train.AdamOptimizer(learning_rate).minimize(loss)
    ```
