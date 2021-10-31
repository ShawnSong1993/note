# AI 

## 1. 简单的拟合

```python
import tensorflow.compat.v1 as tf
import numpy as np
tf.disable_eager_execution()

# create data
x_data = np.random.rand(100).astype(np.float32)   
y_data = x_data*0.1 + 0.3        #生成训练的数据
# create tensorflow struct start

Weights = tf.Variable(tf.random.uniform((1,), -1.0, 1.0))
biases = tf.Variable(tf.zeros((1,)))       #初始化Weights 和 biases   定义变量要用到Variable

y = Weights*x_data + biases
loss = tf.reduce_mean(tf.square(y-y_data))
optimizer = tf.train.GradientDescentOptimizer(0.5)   #指定优化器的类型  0.5为学习率
train = optimizer.minimize(loss)
init = tf.compat.v1.initialize_all_variables()  #初始化所有变量

sess = tf.Session()           #类似声明一个神经网络指针 sess.run()指向哪里，运行哪里
sess.run(init)                #非常重要
for step in range(201):
    sess.run(train)
    # if step % 20 == 0:
    print(step, sess.run(Weights), sess.run(biases))
```

## 2. Session 会话控制

```python
import tensorflow.compat.v1 as tf
import numpy as np
tf.disable_eager_execution()

matrix1 = tf.constant([[3,3]])
matrix2 = tf.constant([[2],[2]])

produc = tf.matmul(matrix1,matrix2)

# method 1                        #方法一的
sess = tf.Session()     
result = sess.run(produc)
print(result)

# method 2
with tf.Session() as sess:
    result = sess.run(produc)
    print(result)
```

## 3. Variable

```python
import tensorflow.compat.v1 as tf
tf.disable_eager_execution()


state = tf.Variable(0,name = 'viriable1')   #通过vairiable函数定义变量，0为定义的初始值

one = tf.constant(1)
# print(state.name)


new_valueble = tf.add(state,one)
update = tf.assign(state,new_valueble)  #赋值函数，将new_valueble赋值给state

init = tf.compat.v1.initialize_all_variables()  #使用Variable函数定义完变量之后必须进行变量初始化

with tf.Session() as sess:
    sess.run(init)
    for _ in range(3):
        sess.run(update)
        print(sess.run(state))

```





















































