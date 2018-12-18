


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

https://course.cse.ust.hk/comp4901j/Password_Only/about/F17fin_key.pdf

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
`tf.cond`

For loops such as $y_t = (y_{t-1} + x_t)*w$ , we use special TF control flow `tf.foldl` (which make dynamic graphs easier in TF through `dynamic batching`)

- Recurrent Networks
- Recursive Networks
- Modular Networks

Caffe Python Interface:
- Interfacing with Numpy
- Extract features: Run net forward
- Compute gradients: Run net backward (DeepDream)
- Deifine Layers in Python with Numpy
- (+) Good for feedforward networks 
- (+) Good for finetuning existing networks
- (+) Train models without writing any code!
- (+) Python interface is pretty useful!
- (+) Can deploy without Python
- (-) Need to write C++ / CUDA for new GPU layers
- (-) Not good for recurrent networks
- (-) Cumbersome for big networks (GoogLeNet, ResNet)

## Topic 9 CNN Architectures

*There could be a CNN Architecture question on exam*

**LeNet-5**
$5\times5$ Conv filters at stride 1
$2\times2$ Sub-sampling (Pooling) layers at stride 2
[Conv-Pool-Conv-Pool-FC-FC]

**AlexNet**
[Conv-Max Pool-Norm-Conv-Max Pool-Norm-3 Convs- Max Pool- 3 FC]

Input $227\times227\times3$
First (Conv): 96 $11\times11$ filters at stride 4
Output: ( (227-11)/4+1 = ) $55 \times 55 \times 96$
Number of Param 11*11*3*96

Second (Max Pool) $3\times3$ filters at stride 2
Output: 27*27*96
Number of Param: 0

[*Need to know output size formula with padding*]

**VGGNet** 16-19 layers
Small filters, Deeper Networks
Only $3\times3$ Conv Stride 1, Pad 1 and $2\times2$ Max Pool stride 2

Stack of three $3\times3$ conv stride 1 layers has same *effective receptive field* as one $7\times7$ conv layer

[*Know how to compute receptive field*]

Fewer parameters: $27C^2$ vs $49C^2$ for C channels per layer

Details: 
- No Local Response Normalization (LRN)
- Use ensembles for best results
- FC7 features generalize well to other tasks
- Similar training procedure as Krizhevsky 2012

**GoogLeNet**

Deeper networks with computational efficiency
- Efficient Inception Module
- No FC Layers
- Only 5m params (12x less than AlexNet)

`Inception module` design a good local network topology

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgyMDI1Mzg1NiwtOTI0OTU1MzYzLC0xMz
E0NDU1NTAsMTA3NDAzNzQ0MCwxNDE1NDE2MDA4LC02Njg2NzMy
MTUsLTQ0MzIwNzg2Nyw3OTQ5NjAxNDcsLTEyOTkxMDY1NzIsMT
U5MDg5MDUzNiwtMjA5NjU0NzcxOCw5NDMxMjM1MzcsLTIxMDc0
MDc4NDEsMjY2NzUyMjUsMTE2NTU0NTg3LDEzODM0Njk4MjgsMT
A0MDY2MzEyNiwtMTYwODIyMzc2Miw5MzI4NDQ4NjcsLTIwMjMw
Nzg2NzNdfQ==
-->