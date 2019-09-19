#### 滑动平均（影子值）：记录了每个参数一段时间内过往值的平均，正价了模型的泛化性。

针对所有参数：w和b（像给参数加了影子，参数变化，影子缓慢追随）

> 影子 = 衰减率*影子+（1-衰减率）×参数  
>影子初值 = 参数初值  
> 衰减率 = min<a href="https://www.codecogs.com/eqnedit.php?latex=\left&space;\{&space;MOVING_AVERAGE_DECAY,\frac{1&plus;a}{10&plus;b}&space;\right&space;\}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\left&space;\{&space;MOVING_AVERAGE_DECAY,\frac{1&plus;a}{10&plus;b}&space;\right&space;\}" title="\left \{ MOVING_AVERAGE_DECAY,\frac{1+a}{10+b} \right \}" /></a>   
> a,b为轮数

MOVING_AVERAGE_DECAY 为0.99，参数w1为0，轮数global_step为0,w1的华东平均值为0参数w1更新为1则：

w1的滑动平均= min(0.99,1/10)*0 + (1-min(0.99,1/10)*1) = 0.9

轮数global_step为100时候，参数w1更新为10则：

w1滑动平均值=min(0.99,101/110)*0.9+(1-min(0.99,101/110)*10) = 0.826 + 0.818 = 1.644

再次运行

w1滑动平均值=min(0.99,101/110)*1.664+(1-min(0.99,101/110)*10) = 2.328

+ ema = tf.train.ExponentialMovingAverage(衰减率MOVING_AVERAGE_DECAY,当前轮数global_step)
    > ema_op = ema.apply([])

+ ema_op = ema.apply(tf.trainable_variables())
    > ema.apply() : 每次运行此句，所有待优化的参数求滑动平均

+ with tf.control_dependencies([train_step, ema_op]) : train_op = tf.no_op(name='train')

    > ema.average(参数名)   
    > 参数名：查看某个参数的滑动平均值:

