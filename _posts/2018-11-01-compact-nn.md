---
layout: single
title:  "Compact Neural Networks"
date:   2018-11-01 10:29:48 +0800
categories: Architecture
---

This section is a summary about the research of compact neural networks. We will focus on:

1. The basic ideas/intuitions behind the paper
2. Space complexity 
3. Computation complexity
4. Structure comparison
5. Evaluation methods
6. (Optional) Explannation of evaluation
7. Drawbacks and some ideas based on the paper

Here are all the papers(models) we will compare:

- Wang, M., Liu, B., CoRR, H. F., 1608.04337, A., 2016. (n.d.). Factorized convolutional neural networks. Openaccess.Thecvf.com
- preprint, F. C. A., 2017. (n.d.). Xception: Deep learning with depthwise separable convolutions. Openaccess.Thecvf.com
- Xie, S., Girshick, R., Dollár, P., and, Z. T. C. V., 2017. (n.d.). Aggregated residual transformations for deep neural networks. Openaccess.Thecvf.com
- Szegedy C, Liu W, Jia Y, et al. Going deeper with convolutions[C]//Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition. 2015: 1-9.
- Szegedy C, Vanhoucke V, Ioffe S, et al. Rethinking the Inception Architecture for Computer Vision[J]. arXiv preprint arXiv:1512.00567, 2015.
- Iandola, F. N., Han, S., Moskewicz, M. W., Ashraf, K., Dally, W. J., & Keutzer, K. (2016, February 24). SqueezeNet: AlexNet-level accuracy with 50x fewer parameters and. arXiv.org.
- Howard, A. G., Zhu, M., Chen, B., Kalenichenko, D., Wang, W., Weyand, T., et al. (2017). MobileNets - Efficient Convolutional Neural Networks for Mobile Vision Applications. CoRR Abs/1509.01626, cs.CV.
- Sandler, M., Howard, A., Zhu, M., Zhmoginov, A., & Chen, L.-C. (2018, January 13). MobileNetV2: Inverted Residuals and Linear Bottlenecks.
- Zhang, X., Zhou, X., Lin, M., & Sun, J. (2017, July 4). ShuffleNet: An Extremely Efficient Convolutional Neural Network for Mobile Devices.
- Zhang, T., Qi, G.-J., Bin Xiao 0001, & Wang, J. (2017). Interleaved Group Convolutions for Deep Neural Networks. CoRR Abs/1509.01626, cs.CV.
- Xie, G., Wang, J., Zhang, T., Lai, J., Hong, R., & Qi, G.-J. (2018, April 17). IGCV$$2$$: Interleaved Structured Sparse Convolutional Neural Networks.
- Sun, K., Li, M., Liu, D., & Wang, J. (2018, June 1). IGCV3: Interleaved Low-Rank Group Convolutions for Efficient Deep Neural Networks. arXiv.org.

TODO:
- [x] Add more networks: Inception series, Xception, SqueezeNet, FactorizedNet
- [ ] Add the parameters and computation analysis about different group splitting method instead of balance splitting.
- [ ] Comparison of computation complexity based on Winograd algorithm.
- [ ] For depthwise convolution, if $$C_o \ne C_i$$, will it be more effient than the combination of linear bottleneck and inverted residuel block?
- [x] Need a uniform mathmatical view to compare different structure.

## Background

### Settings & Assumptions

For the convolution layer, let input $$X \in R^{C_i \times H_x \times W_x}$$ and output $$Y \in R^{C_o \times H_y \times W_y}$$. And let the kernel(weights) $$K \in R^{C_o \times C_i \times H_k \times W_k}$$ for a basic convolution. $$C_i$$ and $$C_o$$ represent the number of input channels and output channels respectively. Besides, $$H_v$$ and $$W_v$$ represent the height and width of variable $$v$$. 

For convinience, we will make strdie $$s=1$$, SAME padding and batch $$B=1$$ for each convolution to compare different models and techniques. And we use General Matrix Matrix Multiplication(GEMM) to compare the computation complexity because there are other optimization for the matrix multiplication, like winograd transform shown in previous paper. And we will ignore the number of parametes and computation for bias. 

*Number of parameters* is represented as #params in this report, which is related to the size of model. Because there are quantization optimization for Neural network, thus to compare the storage size of different models is not a wise option. 

*Computation Complexity* is represented as Multi-Adds (#macs convinience), which is related with the training/inference speed of model. Multi-Adds represents the number of mulplication along with addition and the computation for activation function and BatchNormalization is usually ignored.

### Basic Convolution

For a basic convolution, each output channel is connected with all the input channels, which usually is called dense kernels. 

#### General Matrix Matrix Multiplication

To apply the convolution operation on a 3-D tensor, we usually use img2col to make it as a matrix. After the multiplication, we then use col2img to reform the 3-D tensor. In a mathmatical view, we reshape $$X$$ as $$X'(C_i \times H_k \times W_k, H_y \times W_y)$$ and reshape $$K$$ as $$K'(C_o, C_i \times H_k \times W_k)$$. In this way, we can get the output as $$Y'(C_o, H_y \times W_y)$$ from the matrix multiplication: 

$$$$Y' = K'X'$$$$

Here $$H_y$$ and $$W_y$$ can be calculated by $$H_x$$, $$W_x$$, $$s$$ and padding $$p$$ as shown in a common CNN tutorials. And a more visual perspective can be:

<p align="center">
  <img width="450" height="300" src="https://pic3.zhimg.com/80/6b1dde11bf30688b4f526ea77d54a196_hd.jpg">
</p>

#### Parameters and Computation

\#params=$$C_o \times C_i \times H_k \times W_k$$

\#macs=$$C_o \times C_i \times H_k \times W_k \times H_y \times W_y$$

> By the way, Fully Connected layer can be regarded as a  special convlution where $$H_x=W_x=H_k=W_k=1$$ with stride $$s=0$$ and padding $$p=0$$.

### Group Convolution

The idea was initially proposed by AlexNet paper, which they used this method to train the network on two NVIDIA GPUs. The method is to split input $$X$$ into $$g$$ groups along the channel dimension. For each group, there is a kernel to conduct basic convolution operation inside the group and then concat all the ouputs along channel dimension. In this way, there is no connection among different groups of input and kernels. A visual perspective is that:

<p align="center">
  <img width="450" height="150" src="https://user-images.githubusercontent.com/22738317/32132612-f5294242-bbc6-11e7-9406-3419a2e504cf.png">
</p>

> Usually, people will make the spitting as a balance splitting, that is making the channels in each group the same. However, there is no research on how the splitting method can make the effect on the final performance.

For convenience, we also only account for balance splitting. 

#### Parameters and Computation

\#params=$$(C_o/g \times C_i/g \times H_k \times W_k) \times g = C_o \times C_i \times H_k \times W_k / g$$

\#macs=$$(C_o/g \times C_i/g \times H_k \times W_k \times H_y \times W_y) \times g = C_o \times C_i \times H_k \times W_k \times H_y \times W_y / g$$

Thus, by group convolution, the parameters and computation can be reduced $$\frac{g-1}{g}$$.

### Depthwise Convolution

This method is a extreme case for group convolution, that is the group $$g$$ is exactly the same as the input channels $$C_i$$ and usually $$C_o=C_i$$. Usually it will be followed by a pointwise convolution ($$C_o \times C_i \times 1 \times 1$$) to combine the channels from depthwise convolution, which is called depthwise seperate convolution. We will talk about it in details later.

#### Parameters and Computation

\#params=$$(C_o/g \times C_i/g \times H_k \times W_k) \times g = C_o \times H_k \times W_k$$

\#macs=$$(C_o/g \times C_i/g \times H_k \times W_k \times H_y \times W_y) \times g = C_o \times H_k \times W_k \times H_y \times W_y$$

## Basic Ideas/Intuitions

The general idea is just to construct a structured sparse kernels matrix to reduce number of parameters and computation complexity of dense kernels. Generally, the ideas can be summarized as below:

- extracting spatial and channel information seperately [depthwise + pointwise]
- applying low rank matrix to reduce channels [bottleneck]
- extracting channel information sparsely [group pointwise convoloution]

### FactorizedCNN

*FactorizedCNN* utilizes group convolution but it's a more general than group convolution for pointwise convolution. In details, FactorizedCNN use depthwise convolution to extract spatial information and then reshape channels into s-simentional tensor and connect output with its local neighbors from input channel tensor, like receptive field. A visual perpective can be:

<p align="center">
  <img width="450" height="420" src="https://user-images.githubusercontent.com/33785388/41280887-a52ea832-6e62-11e8-87d2-4d66e190643a.png">
</p>

### ResNeXt

*ResNeXt* is to reduce the parameters and computational complexity by a specific dimension, named Cardinality. It's acctually the same idea as group convolution without information exchanging. Thus we will use $$g$$ to represent the value for Cardinality dimension. ResNeXt is based on the structure of ResNet and sepearte the bottleneck into a grouped bottleneck. Thus the connections/kernels become sparse. A visual perspective can be:

<p align="center">
  <img width="450" height="180" src="https://pbs.twimg.com/media/CxcpH8mXgAAsl1d.jpg">
</p>

Thus, the Cardinality dimension is actually the group number of bottlenecks in ResNet.

### Inception

The basic thoughts behind Inception is to split and then merge, which is focusing on the channel dimension.

#### V1

*Inception V1* uses $$1 \times 1$$, $$3 \times 3$$ and $$5 \times 5$$ convolution and $$3 \times 3$$ pooling layers to increase the width of the network. Output feature maps of each block are the concatenation of those feature maps from each convolution or pooling layer. The visual perspective can be seen as below:

<p align="center">
  <img width="450" height="230" src="https://user-images.githubusercontent.com/13883280/41292295-ba1266d6-6e84-11e8-94c7-efc7967ef83f.png">
</p>

#### V2

*Inception V2* uses 2 $$3 \times 3$$ convolution layers to replace a $$5 \times 5$$ layer, which reduces the number of parameters and speeds up computations. On the other hand, Inception V2 introduces Batch Normalization layer to reduce internel covariate shifts, so the output of every layer follows the N(0, 1) distribution. The visual perspective can be seen as below:

<p align="center">
  <img width="300" height="200" src="https://user-images.githubusercontent.com/13883280/41292302-bd52e9ec-6e84-11e8-80bf-215f1a5364c8.png">
</p>

#### V3

*Inception V3* introduces factorization on $$7 \times 7$$, $$5 \times 5$$ and $$3 \times 3$$ convolutions. It splits $$7 \times 7$$ convolution into 2 1D convolutions, i.e., $$1 \times 7$$ and $$7 \times 1$$ convolution, which can further reduce the number of parameters and speed up computations. Meanwhile, an extra non-linear activation is added to increase the representability of the network. The visual perspective can be seen as below:

<p align="center">
  <img width="600" height="280" src="https://user-images.githubusercontent.com/13883280/41292305-c2168b14-6e84-11e8-9603-fe897b0023c3.png">
</p>

#### V4

*Inception V4* uses a combination of different inception blocks. Each block starts with $$1 \times 1$$ convolutions to reduce the feature dimensions. The visual perspective can be seen as above different Inception-$$X$$ block.

Based on these blocks, the final Inception-V4 can be:

<p align="center">
  <img width="438" alt="screen shot 2018-06-12 at 9 10 24 pm" src="https://user-images.githubusercontent.com/13883280/41292401-0c158116-6e85-11e8-8644-153f470905c3.png">
</p>

### Xception

*Xception* means a extreme Inception nets. Usually, Inception will use $$1 \times 1$$ kernels for each spatial convolution to reduce the number of channels before applying spatial convolution. However, Inception ultilize different size of spatial convolution kernelsand finally concat all the result into feature maps. Based on this, Xception fixes size of spatial convolution kernels as $$3 \times 3$$ for each output channels (depthwise convlution) and then uses only one $$1 \times 1$$ kernels to combine input channels (pointwise convolution). It's actually called depthwise seperate convolution. However, the depthwise seperatable convolution is based in the assumption that the mapping of cross-channels correlations and spatial correlations in the feature maps of convolutional neural networks can be entirely decoupled.

A visual perspective can be:

<p align="center">
  <img width="450" height="220" src="https://vitalab.github.io/deep-learning/images/xception/fig4.png">
</p>

A very important thing for depthwise seperable convolution is that there is no non-linear function after pointwise convolution, which is also different from Inceptions. Besides, the order of convolutions is also different from Inceptions because it will not impact the accuracy. 

### SqueezeNet

*SqueezeNet* adopts $$1 \times 1$$ convolutions as much as possible to reduce the convolution parameters. There is a Fire Module inside SqueezeNet, which contains a squeeze operation that uses $$1 \times 1$$ convolution filters to compress N feature maps into M feature maps (M < N), and an expand operation that contains $$1 \times 1$$ and $$3 \times 3$$ convolution filters to expand feature maps. The outputs from expand operations are concatenated to get the expanded feature maps. A visual perspective of Fire Module can be seen as below:

<p align="center">
  <img width="450" alt="screen shot 2018-06-12 at 2 38 55 pm" src="https://user-images.githubusercontent.com/13883280/41274020-6e7104b6-6e4e-11e8-86ca-95cfe6e8d446.png">
</p>

### MobileNet V1

*MobileNets_V1* applies depthwise seperate convolution to replace the basic convolution and propose two parameters to control the size of network. They are width multiplier and  Resolution Multiplier. 

For depthwise seperate convolution, it consists of depthwise convolution and pointwise convolution. The depthwise convolution is what we have mentioned before. The pointwise convolution is of shape $$(C_o \times,C_i \times 1 \times 1)$$. A visual perspective can be:

<p align="center">
  <img width="450" height="300" src="https://image.slidesharecdn.com/tensorflow-on-android-170806040852/95/tensorflow-on-android-30-638.jpg?cb=1502158423">
</p>

>  The capacity surely is not the same. The depthwise separate convolution is of smaller representative capacity. Because different spatial position may need different filter. However in depthwise separate convolution, the filter is the same for same channel different position. 

> So I think it’s based on the assumption that channel can get same feature although in different spatial. Thus, it's not applicable for the first layer. Can be regarded as one way to reduce parameters in the network. 

<!-- \#params=$$C_i \times H_k \times W_k + C_o \times C_i$$

\#macs=$$C_i \times H_k \times W_k \times H_y \times W_y + C_o \times C_i \times H_y \times W_y$$ -->

First item is for depthwise convolution and second item is for pointwise convolution. Usually $$C_o$$ is much larger than $$H_k \times W_k$$. Thus, the major part of number of parameters and computation is focusing on pointwise convolution. In order to make the computation more efficent, we must make pointwise convolution more compact or even replace it.

The width multiplier $$\alpha$$ is to thin neural network uniformly at each layer. More specificly, input channels and output channels will be multiplier by $$\alpha$$ in each layer. In this way, the parameters and computation can be reduced roughly by $$1-\alpha^2$$.

The resolution multiplier $$\rho$$ is to reduce the representation of input images and internal feature maps. Usually, it will multiply $$H_x$$ and $$W_x$$. it will make no effect on the number of parameters, but it will reduce the computation roughly by $$1-\rho^2$$.

Pointwise convolutions do not require this reordering in memory and can be implemented directly with GEMM which is one of the most optimized numerical linear algebra algorithms because it's actually a matrix and can be mutiplied with the output of depthwise convolutions directly.

*The structure of MobileNet_V1 is from VGG network*

### MobileNet V2

*MobileNet_V2* change the structure of MobileNet_V1 based on the design scheme of ResNet with some modification. It applies the inverted residual with linear bottleneck.

Usually we say that the set of layer activations (for any layer) forms a “manifold of interest”. It has been long assumed that manifolds of interest in neural networks could be embedded in low-dimensional subspaces. 

However, ReLU may cause information loss for the input. Thus, only if the input contains redundent information or can be embedded into a low-dimensional subspaces, we can recover the input with less information loss. A visual perspective can be:

<p align="center">
  <img width="450" height="250" src="https://pic1.zhimg.com/80/v2-e5a07997299057487fe05752cf52fbb4_hd.jpg">
</p>

In this view, MobileNet_V2 chnage the residual block as:

<p align="center">
  <img width="450" height="300" src="https://pic2.zhimg.com/80/v2-5cd17c6e1f812dcf35c119cc7d9347a6_hd.jpg">
</p>

Compared with basic residual block, MobileNet_V2 use the expansion factor (usually $$e=6$$) to increase the output channels from the first pointwise convolution, which can make extracting features more complete. And then it applies the same depthwise convolution followed by pointwise convolution to change back into final less output channels, which is called inverted residual block. However, there is no ReLU after the final pointwise convolution in the inverted residual block of MobileNet_V2, while for residual block there is ReLU after any convolution. In this way, the last convolution can cause less information loss. Thus, for the same task, we can apply smaller width multiplier to get same accuracy because redundent information is transferred from input into internal feature maps in an inverted residual block.

> I think there is another way to keep more redundent information: remove the first pointwise convolution and apply depthwise convolution as a group convolution while for each group, the number of output channels is at least twise of input channels. Try to analize the parameters and computation.

"One interesting property of our architecture is that it provides a natural separation between the input/output domains of the building blocks (bottleneck layers), and the layer transformation – that is a non-linear function that converts input to the output. The former can be seen as the capacity of the network at each layer, whereas the latter as the expressiveness. This is in contrast with tra- ditional convolutional blocks, both regular and separa- ble, where both expressiveness and capacity are tangled together and are functions of the output layer depth."


<!-- \#params=$$eC_i \times C_i + eC_i \times H_k \times W_k + C_o \times eC_i$$

\#macs=$$eC_i \times C_i \times H_x \times W_x + eC_i \times H_k \times W_k \times H_y \times W_y + C_o \times eC_i \times H_y \times W_y$$ -->

In this network, we can also apply width multiplier and resolution multiplier.

*The structure of MobileNet_V1 is from Residual network*

### ShuffleNet

*ShuffleNet* uses shuffled feature maps with group convolution to reduce the computation of normal pointwise convolution. However, in order to make sure that information flow between channel groups. The shuffleNet shuffle the input channels to feed into next group convolution, which usually split each group output into the same number of group and feed them into different group of next group convolution. A visual perspective can be:

<p align="center">
  <img width="600" height="300" src="https://ikhlestov.github.io/images/ML_notes/convolutions/06_shuffled_grouped_convolutions.png">
</p>

Let the number of group be $$g$$ for each ShuffleNet Unit (similar to residual block).

<!-- \#params=$$eC_i \times C_i / g + eC_i \times H_k \times W_k + C_o \times eC_i / g$$

\#macs=$$eC_i \times C_i \times H_x \times W_x / g + eC_i \times H_k \times W_k \times H_y \times W_y + C_o \times eC_i \times H_y \times W_y / g$$ -->

> why not combine group convolution with 3x3, instead of 1x1?
> Because it can reduce the number of parameters.

*The structure of ShuffleNet is from Residual network*


### IGCV1

Actually the main purpose of IGCV1 is to make  the network wider with same number of parameters and computation complexity. In another way, it can benefit from less number of parameters and computation complexity with same width. IGCV1 seperates a dense matrix into the multiplication of two block sparse matrix. For the first matrix, it comes from group spatial convolution. And for the second matrix, it comes from group pointwise convolutiom. In order to make the result of multiplication dense, a permutation matrix is introduced to make each branch of second matrix is connected with all branches (2 branches) in the first matrix. A visual perspective can be:

<p align="center">
  <img width="600" height="200" src="https://user-images.githubusercontent.com/33785388/41323709-dab778aa-6ee2-11e8-916b-c092dee4bdd5.png">
</p>

### IGCV2

*IGCV2* provide a new way to get a dense kernel with fewer parameters and less computation. Instead of connecting all the output channels with input chanels directly, the IGCV2s split the connection into several layers and then increase the connection of each input channel with layer increasing. A visual perspective can be:

<p align="center">
  <img width="600" height="280" src="https://pbs.twimg.com/media/DbCz9ufVAAAosJy.jpg">
</p>

> Actually it's just a extreme case for the connection, but actually we may not need to specify the connection. We can still make the connection as structure sparsity. 

*The structure of IGCV2 is from MobileNet_V1 network*

*The last 3 nets are all to reduce the number of parameters and computation of pointwise convolution.*

### IGCV3

*IGCV3* utilize the bottelneck (low rank matrix) to reduce the compuitation for depthwise convolution. As for the pointwise convolution, it utilize the group convolution with loose commentary condition to make the final weight matrix as a dense matrix. The low rank idea is very similar to matrix decomposition. Actually the work is based on IGCV2 with just an additional bottleneck because IGCV2 can be regarded basing on VGG/Xception or MobileNet_V1. Thus IGCV2 doesn't contain any shotcut connection. A visual perspective can be:

<p align="center">
  <img width="600" height="200" src="https://user-images.githubusercontent.com/33785388/41323729-098a24f2-6ee3-11e8-9df3-e55af2201bd5.png">
</p>

## Mathmatical View

Based on the GEMM, let's see the mathmatical representation of different compact neural networks. Firstly let's introduce a special sparse kernel matrix for $$K'$$.

$$$$
\left[\begin{array}{cccc} 
K^1 & 0 & 0 & 0 \\
0 & K^2 & 0 & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & K^n
\end{array}\right]
$$$$ 

For this type of kernel matrix, $$K^i$$ is actuatlly a smaller matrix, whch can be any shape. Thus the kernel matrix is the block sparse matrix.

And for this part we only account for the calculation and complexity for a unit/block of the whole network with the settings shown previously.

### Inception Series

Hard to give a Normal mathmatical view over them because of different pattern for branches. But the basic idea is low rank matrix for $$1 \times 1$$, $$1 \times n$$ and $$n \times 1$$ kernels.

### SqueezeNet

Similar idea from Inception, but only one $$1 \times 1$$ kernels to reduce the number of channels. It's still utilizing a low rank matrix to reduce number of parameters.

### FactorizedCNN

Decompositing $$K'$$ into $$K'_1$$ and $$K'_2$$, the output $$Y'$$ can be represented as 

$$$$Y' = K'_2K'_1X'$$$$

And the $$K'_1$$ is the block sparse matrix, in which each block is a $$1 \times H_kW_k$$ matrix. It's actually what we called depthwise convolution. And the $$K'_2$$ is a specific sparse matrix. For each line, it's like a dash line for the non-zero elements. Thus, it's not good for hardware acceleration if the locality for output channels is too small. Here we also use $$g$$ symbol, but it's defined as $$g = \frac{C}{C_l}$$, where $$C$$ is the number of input channels and $$C_l$$ is the number of neighbor input channels for each output channel.

### ResNeXt

Ignoring the shotcut connection and decompositing $$K'$$ into $$K'_1$$, $$K'_2$$ and  $$K'_3$$, the output $$Y'$$ can be represented as 

$$$$Y' = K'_3K'_2K'_1X'$$$$

In this case, $$X'$$ needs to be reshaped as $$(C_i, H_x \times W_x)$$ and then $$K'_1$$ is a dense matrix and its first dimension is $$C'_i$$, which is pointwise convolution. Then output of $$K'_1X'$$ needs to be reshaped as $$(C'_i \times H_k \times W_k, H_y \times W_y)$$. Thus $$K'_2$$ is a block sparse matrix with $$\frac{C_o}{g} \times \frac{C'_i}{g}H_kW_k$$ block, which is depthwise convolution. Finally, $$K'_3$$ is a dense matrix, which is pointwise convolution. 

**[Attension]**

- There is a reshape operation for $$K'_1$$ and $$K'_2$$
- There is a ReLU after each matrix multiplication

### Xception

Same analysis as MobileNet_V1

### MobileNet_V1

Decompositing $$K'$$ into $$K'_1$$ and $$K'_2$$, the output $$Y'$$ can be represented as 

$$$$Y' = K'_2K'_1X'$$$$

And the $$K'_1$$ is the block sparse matrix, in which each block is a $$1 \times H_kW_k$$ matrix. It's actually what we called depthwise convolution. And the $$K'_2$$ is a regular dense matrix because the first dimension of output $$K'_1X'$$ is the dimension of output channels. It's actually what we called pointwise convolution. Besides, it finally makes sense for what have been witten in the paper:

>*"1 × 1 convolutions do not require this reordering in memory and can be implemented directly with GEMM which is one of the most optimized numerical linear algebra algorithms"*

**[Attention]**

- There is a ReLU after each matrix multiplication. 

### MobileNet_V2

Ignoring the shotcut connection and decompositing $$K'$$ into $$K'_1$$, $$K'_2$$ and  $$K'_3$$, the output $$Y'$$ can be represented as 

$$$$Y' = K'_3K'_2K'_1X'$$$$

In this case, $$X'$$ needs to be reshaped as $$(C_i, H_x \times W_x)$$ and then $$K'_1$$ is a low rank dense matrix and its first dimension is $$eC_i$$, which is pointwise convolution. Then output of $$K'_1X'$$ needs to be reshaped as $$(eC_i \times H_k \times W_k, H_y \times W_y)$$. Thus $$K'_2$$ is a block sparse matrix with $$1 \times eC_iH_kW_k$$ block, which is depthwise convolution. Finally, $$K'_3$$ is a low rank dense matrix, which is pointwise convolution. 

**[Attension]**

- There is a reshape operation for $$K'_1$$ and $$K'_2$$
- There is a ReLU after $$K'_1X'$$ and $$K'_2K'_1X'$$ not after $$K'_3K'_2K'_1X'$$

### ShuffleNet

Similar to MobileNet_V2, ShuffleNet also decompiste the regular convolution into three convolutions based on Residual Neural Network. However, in order to reduce parameters and computation for $$K'_1$$ and $$K'_2$$, ShuffleNet use group pointwise convolution to replace normal pointwise convolution, which is also trying to construct sparse matrix. 

Thus, in this case the output can be represented as:

$$$$Y' = S(K'_3K'_2S(K'_1X'))$$$$

$$S(*)$$ represnets the shuffle function to shuffle output channels to make sure information flow from different groups. $$K'_2$$ is the same as MobileNet_V2, while $$K'_1$$ and $$K'3$$ are block sparse matrix with $$eC_i/g \times C_i/g$$ and $$C_o/g \times eC_i/g$$ block.

**[Attension]**

- There is a reshape operation for $$K'_1$$ and $$K'_2$$
- There is a ReLU after each matrix multiplication. 

### IGCV2 (similar for IGCV1 and IGCV3)

For IGCV2, it's based on the VGG network or MobileNet_V1 with same input and output channels. Similar to ShuffleNet, IGCV2 replace pointwise convolution into selverl layers of group pointwise convolution to reduce parameters and computation. Thus the output can be represented as:

$$$$Y' = P(\ldots P(K'_3P(K'_2K'_1X'))\ldots)$$$$

$$K'_1$$ represents depthwise convolution as a block sparse matrix. And $$K'_i(i > 1)$$ represents group pointwise convolution as a block sparse matrix. $$P(*)$$ represents the permutation matrix to reorder the channels. However, the main difference with ShuffleNet is that IGCV2 can make sure each output channel is connected with all the input channels while ShuffleNet can not guarantee this. 


## Parameters and Computation

| Models | Parameters | Computation |
|:------:|:----------:|:-----------:|
| Baseline$$^1$$ | $$C_o \times C_i \times H_k \times W_k$$ | $$C_o \times C_i \times H_k \times W_k \times H_y \times W_y$$
| Baseline$$^2$$ | $$C'_i \times C_i + C'_i \times C_i \times H_k \times W_k+ C'_i \times C_o$$ | $$C'_i \times C_i \times H_x \times W_x + C'_i \times C_i \times H_k \times W_k \times H_y \times W_y + C_o \times C'_i \times H_y \times W_y$$ |
| FactorizedCNN$$^1$$ | $$C_i \times H_k \times W_k + C_o \times C_i / g$$ | $$C_i \times H_k \times W_k \times H_y \times W_y + C_o \times C_i \times H_y \times W_y / g$$ |
| ResNeXt$$^2$$ | $$C'_i \times C_i + C'_i \times C_i \times H_k \times W_k /g + C'_i \times C_o$$ | $$C'_i \times C_i \times H_x \times W_x + C'_i \times C_i \times H_k \times W_k \times H_y \times W_y /g + C_o \times C'_i \times H_y \times W_y$$ |
| Xception$$^1$$ | $$C_i \times H_k \times W_k + C_o \times C_i$$ | $$C_i \times H_k \times W_k \times H_y \times W_y + C_o \times C_i \times H_y \times W_y$$ |
| MobileNet_V1$$^1$$ | $$C_i \times H_k \times W_k + C_o \times C_i$$ | $$C_i \times H_k \times W_k \times H_y \times W_y + C_o \times C_i \times H_y \times W_y$$ |
| MobileNet_V2$$^2$$ | $$eC_i \times C_i + eC_i \times H_k \times W_k + C_o \times eC_i$$ | $$eC_i \times C_i \times H_x \times W_x + eC_i \times H_k \times W_k \times H_y \times W_y + C_o \times eC_i \times H_y \times W_y$$ |
| ShuffleNet$$^2$$ | $$eC_i \times C_i / g + eC_i \times H_k \times W_k + C_o \times eC_i / g$$ | $$eC_i \times C_i \times H_x \times W_x / g + eC_i \times H_k \times W_k \times H_y \times W_y + C_o \times eC_i \times H_y \times W_y / g$$ |
| IGCV1$$^1$$ | $$C_i \times C_i \times H_k \times W_k / g_1 + C_i \times C_o / g_2$$ | $$C_i \times C_i \times H_k \times W_k \times H_y \times W_y / g_1 + C_o \times C_i \times H_y \times W_y / g_2$$ |
| IGCV2$$^1$$ | $$C_i \times H_k \times W_k + \log(C_i) \times C_i^{1+\frac{1}{\log(C_i)}}$$ | 
| IGCV3 |

Here baseline$$^1$$ is based on the normal/regular convolutional layer and baseline$$^2$$ is based on the bottlenect block of Resnet. And all model_name$$^1$$ means its unit is just based on regular convolution and model_name$$^2$$ means its unit is a bottleneck block as in ResNet. An example for bottlenect block of Resnet can be:

<p align="center">
  <img width="220" height="200" src="https://www.safaribooksonline.com/library/view/building-machine-learning/9781786466587/graphics/image_08_008.jpg">
</p>

## High Level View

Inception series, SqueezeNet, ResNeXt, Xception and MobileNets can all be regarded as a sequential work on how to seperate convolution into pointwise convolution and depthwise convolution to some extends.

However, FactorizedNet, ShuffleNet and IGCVs can be regarded as the improvements on the pointwise convolution. And all these three types of work can be generalized into a more general method, which I name it as convolution in convolution (CIC). 

As shown in FatorizedNet, the input channel dimension will be expanded as multi-dimentional tensor. In this way, FatorizedNet utilize local connections (like a receptive filed) to get one output channel. However, the detailed method for expanding hasn't been referred in the paper and it's also very hard to decide. 

Based on the same idea, ShuffleNet and IGCVs can be redefined. Let $$g_i$$ be the number of groups for input channels and $$g_o$$ be the number of output channels.

For a single group pointwise convolution, the input channel dimension can be regarded as $$C_i/g_i \times g_i$$. Thus it's just a $$C_o/g_o \times 1 \times g_i$$ kernel on reshaped input channel with stride equal to 1 only for the first dimension of reshaped input channel. A visual perspective can be:



### ShuffleNet

For ShuffleNet, we can reshape input channel dimension into $$(g_i \times C_i/g_i)$$. For the combination of channel shuffle and group pointwise convolution, it's just the a $$C_o/g_o \times g_i \times C_i/(g_ig_o)$$ kernels on reshaped input channel dimension with convolution of stride equal to 1 for the second dimension of reshaped input channel. A visual perspective can be:

It assumes that the channels for the same group can share similar features, Thus the channel shuffle can be effective for group communication.


### IGCVs

For IGCV2, input channel dimension can be reshaped as $$g_i \times 2$$. Thus $$g_i \times 2 = C_i$$ should hold. Thus the combination of permutation and group convolution can be regarded as a $$2 \times 2 \times 1$$ kernel on reshaped input channel with concolution of stride equal to (2, 1) for the fist and second dimenson of reshaped input channel. A visual pespective can be:

It also shares similar assumption as ShuffleNet.

## Structures

<p align="center">
  <img width="600" height="300" src="https://stanford.edu/~songhan/squeezenet.jpg">
  <img width="500" height="300" src="https://cdn-images-1.medium.com/max/1600/1*mdiQTfovOXKnqzfj727b9Q.png">
  <img width="500" height="300" src="https://pic3.zhimg.com/80/v2-b5af2ae3e210901ec31c79dc1e395fab_hd.jpg">
  <img width="400" height="300" src="https://raw.githubusercontent.com/joshua19881228/my_blogs/master/Computer_Vision/Reading_Note/figures/Reading_Note_20170720_ShuffleNet_1.png">
  <img width="470" height="300" src="https://pic3.zhimg.com/80/v2-0c13ea954916e00355bd0e86d185cf7a_hd.jpg">
</p>

## Evaluation