


> Written with [StackEdit](https://stackedit.io/).

https://www.mergersandinquisitions.com/quant-hedge-funds/

# COMP4901j Final Review

## Some References

Some practice problem here http://dl.ee.cuhk.edu.hk/

http://cs231n.stanford.edu/syllabus.html

Machine Learning,  [Tom Mitchell](http://www.cs.cmu.edu/~tom),

Machine Learning: A Probabilistic Perspective, Kevin Murphy



## Possible Exams
https://people.eecs.berkeley.edu/~jrs/189/exam/finalf15blank.pdf

http://www.cs.cmu.edu/~10701/previous.html

http://www.cs.cmu.edu/~aarti/Class/10601/prev.shtml

https://www.analyticsvidhya.com/blog/2017/01/must-know-questions-deep-learning/

http://web.mit.edu/6.034/wwwbob/recitation8-fall11.pdf

http://courses.csail.mit.edu/6.034s/resources.html

https://ai6034.mit.edu/wiki/index.php?title=Reference_material_and_playlist

## Topic 8 Deep Learning Software

CPU: Fewer Cores, Each core is much faster and much more capable; great at sequential tasks
GPU: More Cores, but each core is much slower and "dumber"; great for parallel tasks

Training can bottleneck on reading data and transferring to GPU!

Solutions:
- Read all data into RAM
- Use SSD instead of HDD
- Use multiple CPU threads to pre-fetch data

Deep Learning Frameworks:
- Easily build big computational graphs
- Easily compute gradients in computational graphs
- Run it all efficiently on GPU

Computational Graphs:
- Cannot run on GPU
- Have to compute own gradients

[TensorFlow Example] Train a two-layer ReLU network on random data with L2 Loss

what is `tf.reduce_mean`?

Problem with `tf.placeholder` (fed on each call); copying weights between CPU/GPU each step is heavy. Use `tf.Variable` instead (persists in the graph between calls).

`assign()` operation. Also need a dummy graph node that depends on updates. 

Gradients can also be computed and weights can be updated with an optimizer.

    N, D, H = 
    x = tf.placeholder(tf.float32, shape=(N,D))
    y = tf.placeholder(tf.float32, shape=(N,D))
    w1 = tf.Variable(tf.random_normal((D,H)))
    w2 = tf.Variable(tf.random_normal((H,D)))
    
    h = tf.maximum(tf.matmul(x,w1),0)
    y_pred = tf.matmul(h,w2)
    loss = tf.losses.mean_squared_error(y_pred,y)
    #diff = y_pred - y
    #loss = tf.reduce_mean(tf.reduce_sum(diff*diff, axis=1))

`Keras`: High-level Wrapper

PyTorch: Three Levels of Abstraction
- Tensor: Imperative ndarray; but runs on GPU (Numpy Array)
- Variable: Node in a computational  graph; stores data and gradient (Tensor, Variable, Placeholder)
- Module: A neural network layer; may store state or learnable weights (tf.layers, TFSlim, TFLearn)

PyTorch Variables remember how they were created. `requires_grad=False` or `True`

`DataLoader` wraps a data-set and provides minibatching, shuffling, multithreading. We can iterate over `loader` to form minibatches

**Static vs Dynamic Graphs**
TF: Build graph once, then run many times
PyTorch: Each forward pass defines a new graph

With static graphs, the graph can be *optimized* before it runs. Fused operations to equivalent graph

**Static**: Once graph is built, can *serialize* it and run it without the code that built the graph. **Dynamic**: Graph building and execution are intertwined, so always need to keep code around.

In PyTorch, Conditional is like normal Python. But in TF, special TF control flow operator should be applied.






<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE2NTU0NTg3LDEzODM0Njk4MjgsMTA0MD
Y2MzEyNiwtMTYwODIyMzc2Miw5MzI4NDQ4NjcsLTIwMjMwNzg2
NzMsMzc0MDE3ODI1LC05MzkxODcwNDUsLTEzMTA3NjIwMzcsLT
EyOTc2NTcwNjEsLTEyMzIwMjU0MDAsLTQyOTY4NTI2MSw4MzIw
Nzk3MjcsMjkzNzIxNDczLDMxOTc0MzY4MCwxMDc3MTE3ODE4LC
0xMzg2NTgxOTY1LDE4ODE4NjA0NzUsMTc1NzcxMTg2XX0=
-->