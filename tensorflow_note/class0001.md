#### 正则化缓解过拟合

正则化在损失函数中引入模型复杂指标，利用***给W加权值*** ,弱化了训练数据的噪声（一般不正则化b）

<a href="https://www.codecogs.com/eqnedit.php?latex=loss&space;=&space;loss(y,y_{1})&plus;REGULARIZER*loss(w)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?loss&space;=&space;loss(y,y_{1})&plus;REGULARIZER*loss(w)" title="loss = loss(y,y_{1})+REGULARIZER*loss(w)" /></a>

> loss(y,y1) :模型中所有参数的损失函数如：交叉熵、均方误差

> REGULARIZER: 用超参数REGULARIZER给出参数w在用loss中的比例，即正则化的权重

> w: 需要正则化的参数

loss(w) = tf.contrib.layers.l1_regularizer(REGULARIZER)(w)


<a href="https://www.codecogs.com/eqnedit.php?latex=loss_{L1}(w)&space;=&space;\sum_{i=0}^{n}&space;\left&space;|&space;w_{i}&space;\right&space;|" target="_blank"><img src="https://latex.codecogs.com/gif.latex?loss_{L1}(w)&space;=&space;\sum_{i=0}^{n}&space;\left&space;|&space;w_{i}&space;\right&space;|" title="loss_{L1}(w) = \sum_{i=0}^{n} \left | w_{i} \right |" /></a>


loss(w) = tf.contrib.layers.l2_regularizer(REGULARIZER)(w)

<a href="https://www.codecogs.com/eqnedit.php?latex=loss_{L2}(w)&space;=&space;\sum_{i=0}^{n}&space;\left&space;|&space;w_{i}^{2}&space;\right&space;|" target="_blank"><img src="https://latex.codecogs.com/gif.latex?loss_{L2}(w)&space;=&space;\sum_{i=0}^{n}&space;\left&space;|&space;w_{i}^{2}&space;\right&space;|" title="loss_{L2}(w) = \sum_{i=0}^{n} \left | w_{i}^{2} \right |" /></a>

+ tf.add_to_collection('losses',tf.contrib.layers.l2_regularizer(regularizer)(w))

+ loss = cem + tf.add_n(tf.get_collection('losses'))

