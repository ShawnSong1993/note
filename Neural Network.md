# Neural Network 

## 1. 学习资料

![](/home/sxg/Pictures/Screenshot%20from%202021-08-31%2009-04-07.png)

<img src="https://gitee.com/ShawnSong1993/data/raw/master/pic/Screenshot from 2021-08-31 09-33-08.png" style="zoom:67%;" />

1. [吴恩达的深度学习](https://www.deeplearning.ai/)

## 2. Session

Session 类似于一个指针

Session 有两种形式

```Python
import tensorflow.compat.v1 as tf
import numpy as np
tf.disable_eager_execution()
matrix1 = tf.constant([[3,3]])
matrix2 = tf.constant([[2],[2]])
produc = tf.matmul(matrix1,matrix2)

# method 1    
sess = tf.Session()
result = sess.run(produc)
print(result)
# method 2
with tf.Session() as sess:
    result = sess.run(produc)
    print(result)
```

## 3. Variable

TensorFlow 中定义变量时，使用tf.Variable()定义，定义完成后要使用initialize_all_variables()进行初始化

```Python
import tensorflow.compat.v1 as tf
tf.disable_eager_execution()

state = tf.Variable(0,name = 'viriable1')
one = tf.constant(1)

new_valueble = tf.add(state,one)
update = tf.assign(state,new_valueble)
init = tf.compat.v1.initialize_all_variables()
with tf.Session() as sess:
    sess.run(init)
    for _ in range(3):
        sess.run(update)
        print(sess.run(state))
```

## 4. Placeholder

placeholder是在定义变量，在执行运算的时候才开始赋值，并以字典的形式进行赋值

```python
import tensorflow.compat.v1 as tf
tf.disable_eager_execution()

input1 = tf.placeholder(tf.float32)
input2 = tf.placeholder(tf.float32)

out = tf.multiply(input1,input2)

with tf.Session() as sess:
    print(sess.run(out,feed_dict={input1:[3.0],input2:[2.0]})) #feed_dict是以字典的形式赋值
```

## 5. Active function

y=wx: 

W: 需要的参数（固定的数）

X: 输入值

y: 预测值

y = AF(wx)

AF: active function, 常用有三种，也可以定义自定义激励函数，定义的函数需要可微

![](https://gitee.com/ShawnSong1993/data/raw/master/pic/Screenshot from 2021-09-07 20-30-32.png)





























