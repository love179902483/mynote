#### 学习率

> 学习率learning_rate:每次参数更新的幅度

<a href="https://www.codecogs.com/eqnedit.php?latex=w_{n&plus;1}&space;=&space;w_{n}&space;-&space;learning_rate\bigtriangledown" target="_blank"><img src="https://latex.codecogs.com/gif.latex?w_{n&plus;1}&space;=&space;w_{n}&space;-&space;learning_rate\bigtriangledown" title="w_{n+1} = w_{n} - learning_rate\bigtriangledown" /></a>

> wn+1 :更新后的参数

> wn : 当前参数

> learning_rate ：学习率

> <a href="https://www.codecogs.com/eqnedit.php?latex=\bigtriangledown" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\bigtriangledown" title="\bigtriangledown" /></a> : 损失函数的梯度(导数) 


eg: 损失函数 <a href="https://www.codecogs.com/eqnedit.php?latex=loss&space;=&space;(w&plus;1)^{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?loss&space;=&space;(w&plus;1)^{2}" title="loss = (w+1)^{2}" /></a> 梯度: <a href="https://www.codecogs.com/eqnedit.php?latex=\bigtriangledown&space;=&space;\frac{\partial&space;loss}{\partial&space;w}&space;=&space;2w&space;&plus;&space;2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\bigtriangledown&space;=&space;\frac{\partial&space;loss}{\partial&space;w}&space;=&space;2w&space;&plus;&space;2" title="\bigtriangledown = \frac{\partial loss}{\partial w} = 2w + 2" /></a>

参数w初始化为5，学习率为0.2则:

| 次数   | 参数       | 结果                      |
|--------|------------|---------------------------|
| 第一次 | 参数w:5    | 5-0.2*(2*52)=2.6          |
| 第二次 | 参数w:2.6  | 2.6-0.2*(2*2.6+2)=1.16    |
| 第三次 | 参数w:1.16 | 1.16-0.2*(2*1.16+2)=0.296 |
| ....   | .....      | .....                     |

***优化参数的目的是为了更好找到使loss函数最小的点***

#### 学习率设置多少合适？
依旧以<a href="https://www.codecogs.com/eqnedit.php?latex=loss&space;=&space;(w&plus;1)^{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?loss&space;=&space;(w&plus;1)^{2}" title="loss = (w+1)^{2}" /></a>为例

开始令learning_rate = 1

只有令learning_rate = 0.001

> 学习率打了震荡不收敛，学习率小了收敛速度慢。

#### 指数衰减学习率

learning_rate = LEARNING_RATE_BASE.LEARNING_RATE_DECARY <a href="https://www.codecogs.com/eqnedit.php?latex=\frac{global_Step}{LEARNING_RATE_STPE}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{global_Step}{LEARNING_RATE_STPE}" title="\frac{global_Step}{LEARNING_RATE_STPE}" /></a><Paste>

> LEARNING_RATE_BASE： 学习率基数，学习率初始值

> LEARNING_RATE_decary ： 学习率衰减率(0,1)

> <a href="https://www.codecogs.com/eqnedit.php?latex=\frac{global_Step}{LEARNING_RATE_STPE}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{global_Step}{LEARNING_RATE_STPE}" title="\frac{global_Step}{LEARNING_RATE_STPE}" /></a><Paste>  

> global_step : 运行了几轮BATCH_SIZE

> LEARNING_RATE_STPE ：多少轮更新一次学习率 = 总体样本数/BATCH_SIZE

global_step = tf.Variable(0, trainable = False)

learning_rate = tf.train.exponential_decay(LEARNING_RATE_BASE, global_step, LEARNING_RATE_STEP, LEARNING_RATE_DECAY, staircase = True)

> staircase=True : False/True
