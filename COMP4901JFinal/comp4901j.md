


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

`Inception module` design a good local network topology (network within a network) an then stack these modules on top of each other

![NaiveInception](/Users/stephen/Desktop/Workspace/MarkdownNotes/COMP4901JFinal/img/NaiveInception.png)

The computational complexity is its problem.

>  Conv Ops = Output size $\times$ Filter size

Pooling layer also preserves feature depth, which means total depth after concatenation can only grow at every layer.

Solution: `Bottleneck` layers that use $1\times1$ convolutions to reduce feature depth.

Suppose $56\times56\times64$ input, $1\times1$ CONV with 32 filters, each filter has size $1\times1\times64$ and performs a 64-dimensional dot product, Output is $56\times56\times32$

Preserves spatial dimensions, reduces depth, projects depth to lower dimension (combination of feature maps)

![Inception](/Users/stephen/Desktop/Workspace/MarkdownNotes/COMP4901JFinal/img/Inception.png)

[*Calculate Number of Conv Ops*]

Less Conv Ops and Reduce Depth



**ResNet**

Very deep network using residual connections

![DepthProblem](/Users/stephen/Desktop/Workspace/MarkdownNotes/COMP4901JFinal/img/DepthProblem.png)

Hypothesis: the problem is an optimization problem, deeper models are harder to
optimize. The deeper model should be able to perform at least as well as the shallower model.

A solution by construction is copying the learned layers from the shallower model and setting additional layers to identity mapping.

![ResBlock](/Users/stephen/Desktop/Workspace/MarkdownNotes/COMP4901JFinal/img/ResBlock.png)

For deeper networks, use `bottleneck` layer to improve efficiency (similar to GoogLeNet)



Other architectures to keep in mind are:

- NiN
- Wide ResNet
- ResNeXT
- Stochastic Depth
- DenseNet
- FractalNet
- SqueezeNet



## Topic 10 Recurrent Neural Network

![RNNSequence](/Users/stephen/Desktop/Workspace/MarkdownNotes/COMP4901JFinal/img/RNNSequence.png)

Image Captioning -> Sentiment Classification -> Machine Translation -> Video Classification on frame level

Sequential Processing of Non-Sequence Data


We can process a sequence of vectors $\bar{x}$ by applying a recurrence formula at every time step: 
$$h_t = f_W(h_{t-1},x_t)$$
new state, some function with param W, old state, input vector at some time step

**Vanilla Recurrent Neural Network**
$h_t = tanh(W_{hh}h_{t=1}+W_{xh}x_t)$
$y_t = W_{hy}h_t$

[Many to One] Encode input sequence in a single vector
[One to Many] Produce output sequence from single input vector

At test-time sample characters one at a time, feed back to model.

Backprop through time
Forward through entire sequence to compute loss, then backward through entire sequence to compute gradient

Truncated Backprop through time
Run forward and backward through chunks of the sequence instead of whole sequence

Carry hidden states forward in time forever, but only back-prop for some smaller number of steps

*Image Captioning with Attention*:
RNN focuses its attention at a different spatial location when generating each word.
[Image Lecture 10 P83]

Multilayer RNNs 
[Image Lecture 10 P89]

Vanilla RNN Gradient Flow
Backprop from $h_t$ to $h_{t-1}$ multiplies by $W$ (actually $W^T_{hh}$)
Computing gradient of $h_0$ involves many factors of $W$ and repeated tanh

Exploding gradients: Gradient Clipping: Scale gradient if its norm is too big.
Vanishing gradients: Change RNN Architecture

[Image Lecture 10 P99]
[Image Lecture 10 P102]
[Image Lecture 10 P103] `GRU`

## Topic 11 Detection and Segmentation

Semantic Segmentation, Classification+Localization, Object Detection, Instance Segmentation

*Semantic Segmentation* Label each pixel in the image with a category label. Do not differentiate instances, only care about pixels

Idea1: sliding window on extracted patches
Problem: Very inefficient! Not reusing shared features between overlapping patches

Idea2: Full Convolution, Design a network as a bunch of convolutional layers to make predictions for pixels all at once!
Problem: convolutions at original image resolution are expensive
Solution: Design network as a bunch of convolutional layers, with `downsampling` and `upsampling` 

Downsampling: Pooling, Strided Convolution
Upsamling: `Nearest Neighbor`, `"Bed of Nails"`, `Max Unpooling` (Remember which element was max), `Max Pooling` (Use positions from pooling layer)

`Transpose Convolution` 
Input gives weight for the filter, weighted sum where output overlaps, Filter moves 2(stride) pixels in the output for every one pixel in the input, **Stride gives ratio between movement in output and input**
 
`conv1d_transpose`
Output contains copies of the filter weighted by the input, summing at overlaps in the output, **Need to crop on pixel from output to make output exactly 2$\times$ input**

Convolution as Matrix Multiplication
[Image Lecture 11 P41]

*Classification+Localization*
Treat localization as a regression problem

`Multitask Loss` Softmax Loss for Class Label
L2 Loss for Box Coordinates

*Human Pose Estimation* 

*Object Detection as Classification*
Sliding Window: Apply a CNN to many different crops of the image, CNN classifies each crop as object or background.

Problem: Need to apply CNN to huge number of locations and scales, very computationally expensive.

`Region Proposal` Find blobby image regions that are likely to contain objects
Relatively fast to run; Selective Search gives 1000 region proposals in a few seconds on CPU

[Lecture 11 P63] RCNN

## Topic 12 Visualizing and Understanding



## Topic 13 Generative Models

Last Layer: L2 Nearest Neighbors in feature space
4096-dimensional vector for an image

Dimensionality Reduction: PCA or T

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg3NjAwODI0Myw4NDU5Mjg1MzAsNzU0MT
I5NjczLC0xMjE1Mjk0ODk1LDk5ODkxMTg3OSwxOTM1OTUyOTE0
LC0xMDcyNzAwNjU0LDEzMTY1NTY4MjksMzQwNTYxMDQ2LDQxND
g3MTYwOSwtNjI0NzAxNzUxLDI0MDY0OTkxMSwtMTc2MTQwNzY3
MSwtMjA2NzIxNTY2NCwtMTA1MDE4MzkxMywxMjU2ODk3NTU1LD
IwMjIzMjY2NjEsLTkyNDk1NTM2MywtMTMxNDQ1NTUwLDEwNzQw
Mzc0NDBdfQ==
-->