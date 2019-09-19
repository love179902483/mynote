#### 神经元模型之前课程的：
<a href="https://www.codecogs.com/eqnedit.php?latex=\sum_{i=1}^{n}&space;x_{i}w_{i}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sum_{i=1}^{n}&space;x_{i}w_{i}" title="\sum_{i=1}^{n} x_{i}w_{i}" /></a>

#### 1943年 McCulloch Pitts 神经元模型：

<a href="https://www.codecogs.com/eqnedit.php?latex=f&space;\left&space;(&space;\sum_{i=1}^{n}&space;x_{i}w_{i}&space;&plus;&space;b&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f&space;\left&space;(&space;\sum_{i=1}^{n}&space;x_{i}w_{i}&space;&plus;&space;b&space;\right&space;)" title="f \left ( \sum_{i=1}^{n} x_{i}w_{i} + b \right )" /></a>

> f：为激活函数(activaation function)  

> bias：篇置项

#### 激活函数 activation function 

+ relu 
    > tf.nn.relu()

    <a href="https://www.codecogs.com/eqnedit.php?latex=f(x)=max(x,0)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f(x)=max(x,0)" title="f(x)=max(x,0)" /></a>

+ sigmoid
    > tf.nn.sigmoid()

    <a href="https://www.codecogs.com/eqnedit.php?latex=f(x)=\frac{1}{1&plus;e^{-x}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f(x)=\frac{1}{1&plus;e^{-x}}" title="f(x)=\frac{1}{1+e^{-x}}" /></a>

+ tanh
    > tf.nn.tanh()

    <a href="https://www.codecogs.com/eqnedit.php?latex=f(x)=\frac{1-e^{^{-2x}}}{1&plus;e^{-2x}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f(x)=\frac{1-e^{^{-2x}}}{1&plus;e^{-2x}}" title="f(x)=\frac{1-e^{^{-2x}}}{1+e^{-2x}}" /></a>

#### NN复杂度：多用NN层数和NN参数的个数表示

+ 层数 = 隐藏层的层数+1个输出层
+ 总参数 = 总W + 总b
![avatar](https://i.imgur.com/4Lh222M.png)


#### 顿时函数loss、学习率learning_rate、滑动平均ema、正则化regularization

+ 损失函数(loss): 预测值(y)与已知答案(y1)的差距

    NN优化目标：loss最小

     + mse(Mean Squared Error) 
     + 自定义
     + ce(Cross Entropy)

+ 均方误差mse: 

    <a href="https://www.codecogs.com/eqnedit.php?latex=MSE(y_{1},y)&space;=&space;\frac{&space;\sum_{i=1}^{n}&space;\left&space;(&space;y_{1}-y&space;\right&space;)^{2}&space;}{n}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?MSE(y_{1},y)&space;=&space;\frac{&space;\sum_{i=1}^{n}&space;\left&space;(&space;y_{1}-y&space;\right&space;)^{2}&space;}{n}" title="MSE(y_{1},y) = \frac{ \sum_{i=1}^{n} \left ( y_{1}-y \right )^{2} }{n}" /></a>

    loss_mse = tf.reduce_mean(tf.square(y1-y))

> 预测酸奶日销量y. x1、x2是影响日销量的因素

> 建模前，应该预先采集的数据有：每日x1、x2和销量y1（即已知答案，最佳情况：产量=销量）拟造数据X,Y1：y1=x1+x2 噪声： -0.05～+0.05 拟合可以预测销量的函数
  
+ 自定义损失函数：
    
    如果预测商品销量，预测多了，损失成本；预测少了，损失利润。若利润!=成本，则mse产生的loss无法利益最大化。
    
    自定义损失函数 ： <a href="https://www.codecogs.com/eqnedit.php?latex=loss(y_{1},y)&space;=&space;\sum_{n}^{}&space;f(y_{1},y)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?loss(y_{1},y)&space;=&space;\sum_{n}^{}&space;f(y_{1},y)" title="loss(y_{1},y) = \sum_{n}^{} f(y_{1},y)" /></a>
   
    > y1:标准答案的数据集

    > y2:预测答案的数据集


   <a href="https://www.codecogs.com/eqnedit.php?latex=f(y_{1},y)&space;=&space;\left\{\begin{matrix}&space;PROFIT*(y_{1}-y)&space;y<y_{1}&space;\\&space;COST*(y-y_{1})&space;y>=y_{1}&space;\end{matrix}\right." target="_blank"><img src="https://latex.codecogs.com/gif.latex?f(y_{1},y)&space;=&space;\left\{\begin{matrix}&space;PROFIT*(y_{1}-y)&space;y<y_{1}&space;\\&space;COST*(y-y_{1})&space;y>=y_{1}&space;\end{matrix}\right." title="f(y_{1},y) = \left\{\begin{matrix} PROFIT*(y_{1}-y) y<y_{1} \\ COST*(y-y_{1}) y>=y_{1} \end{matrix}\right." /></a>

   预测的y少了，损失利润（PROFIT）

   预测的y多了，损失成本(COST)

   loss = tf.reduce_sum(tf.where(tf.greater(y,y1),COST(y-y1),PROFIT(y1-y)))

   > 如：预测酸奶销量，酸奶成本（cost)1元，酸奶利润（profit）9元。

   > 预测少了损失利润9元，大于预测多了损失成本1元。

   > 预测少了损失大，希望生成的预测函数往多了预测。


+ 交叉熵ce(Cross Entropy): 表征两个概率分布之间的距离     
   <a href="https://www.codecogs.com/eqnedit.php?latex=H(y_{1},y)&space;=&space;-\sum&space;y_{1}*log^{y}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H(y_{1},y)&space;=&space;-\sum&space;y_{1}*log^{y}" title="H(y_{1},y) = -\sum y_{1}*log^{y}" /></a>

   eg: 二分类一直答案y_=(1,0) 预算y1 = (0.6,0.4) y2 = (0.8, 0.2) 哪个更接近标准答案？

   <a href="https://www.codecogs.com/eqnedit.php?latex=H_{1}((1.0),(0.6,0.4))&space;=&space;-(1*log^{0.6}&space;&plus;&space;0*log^{0.4})&space;\approx&space;-(-0.222&space;&plus;&space;0)&space;=&space;0.222" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H_{1}((1.0),(0.6,0.4))&space;=&space;-(1*log^{0.6}&space;&plus;&space;0*log^{0.4})&space;\approx&space;-(-0.222&space;&plus;&space;0)&space;=&space;0.222" title="H_{1}((1.0),(0.6,0.4)) = -(1*log^{0.6} + 0*log^{0.4}) \approx -(-0.222 + 0) = 0.222" /></a>

   <a href="https://www.codecogs.com/eqnedit.php?latex=H_{1}((1.0),(0.8,0.2))&space;=&space;-(1*log^{0.8}&space;&plus;&space;0*log^{0.2})&space;\approx&space;-(-0.097&space;&plus;&space;0)&space;=&space;0.097" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H_{1}((1.0),(0.8,0.2))&space;=&space;-(1*log^{0.8}&space;&plus;&space;0*log^{0.2})&space;\approx&space;-(-0.097&space;&plus;&space;0)&space;=&space;0.097" title="H_{1}((1.0),(0.8,0.2)) = -(1*log^{0.8} + 0*log^{0.2}) \approx -(-0.097 + 0) = 0.097" /></a>

   所以y2预测更准确

   ce = -tf.reduce_mean(y_*tf.log(tf.clip_by_value(y, 1e-12, 1.0)))
   > tf.clip_by_value(y,1e-12, 1.0)  => y小于1e-12为1e-12大于1.0为1.0

+ 当n分类的n个输出（y1,y2,.....yn）通过softmax()函数，便满足了概率分布的要求：

   <a href="https://www.codecogs.com/eqnedit.php?latex=\forall&space;x&space;P(X=x)\epsilon&space;[0,1]" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\forall&space;x&space;P(X=x)\epsilon&space;[0,1]" title="\forall x P(X=x)\epsilon [0,1]" /></a>
   并且
   <a href="https://www.codecogs.com/eqnedit.php?latex=\sum_{x}^{}P(X&space;=&space;x)&space;=&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sum_{x}^{}P(X&space;=&space;x)&space;=&space;1" title="\sum_{x}^{}P(X = x) = 1" /></a>

+ <a href="https://www.codecogs.com/eqnedit.php?latex=softmax(y_{i})&space;=&space;\frac{e^{y_{i}}}{\sum_{j=1}^{n}e^{y_{j}}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?softmax(y_{i})&space;=&space;\frac{e^{y_{i}}}{\sum_{j=1}^{n}e^{y_{j}}}" title="softmax(y_{i}) = \frac{e^{y_{i}}}{\sum_{j=1}^{n}e^{y_{j}}}" /></a>

    ce = tf.nn.sparse_softmax_cross_entropy_with_logits(logits=y,labels=tf.argmax(y_,1))

    cem = tf.reduce_mean(ce)

----
### 这里不明白啥意思
![avatar](https://i.imgur.com/A9IqM1z.png)
   






