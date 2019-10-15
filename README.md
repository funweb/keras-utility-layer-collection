# Keras Utility & Layer Collection [WIP]
Collection of custom layers for Keras which are missing in the main framework. These layers might be useful to reproduce current state-of-the-art deep learning papers using Keras.

Keras的自定义层集合，主框架中缺少这些自定义层。这些层次可能对使用Keras复制当前最先进的深度学习论文有用。

## Applications

Using this library the following research papers have been reimplemented in Keras:

利用这个图书馆，以下研究论文已在Keras重新实现:

- [Attention is all you need](https://github.com/FlashTek/attention-is-all-you-need-keras)
- [Show, attend and tell](https://github.com/FlashTek/show-attend-and-tell-keras)

## Overview of implemented Layers

At the moment the `Keras Layer Collection` offers the following layers/features:

目前，“ Keras图层集合”提供以下图层/功能： 

- [Scaled Dot-Product Attention](#sdpattention)
- [Multi-Head Attention](#mhatn)
- [Layer Normalization](#layernorm)
- [Sequencewise Attention](#seqatn)
- [Attention Wrapper](#atnwrapper)

### Scaled Dot-Product Attention <a name="sdpattention"></a>

Implementation as described in [Attention Is All You Need](https://arxiv.org/abs/1706.03762). Performs a non-linear transformation on the values `V` by comparing the queries `Q` with the keys `K`. The illustration below is taken from the paper cited above.

实现了论文中所说的[Attention Is All You Need](https://arxiv.org/abs/1706.03762)的方法。通过比较查询Q和键k，对值V进行非线性转换。下面的插图取自上面引用的论文。

<img src="https://i.imgur.com/7zDGedN.jpg" height=250>

### Multi-Head Attention <a name="mhatn"></a>
Implementation as described in [Attention Is All You Need](https://arxiv.org/abs/1706.03762). This is basically just a bunch a [Scaled Dot-Product Attention](#sdpattention) blocks whose output is combined with a linear transformation. The illustration below is taken from the paper cited above.

您只需要注意中描述的实现。这基本上就是一堆按比例缩放的网络产品注意力块，其输出与线性变换相结合。下面的插图取自上面引用的论文。

<img src="https://i.imgur.com/c0xLAfS.jpg" height=250>

### Layer Normalization <a name="layernorm"></a>


### Sequencewise Attention <a name="seqatn"></a>
This layer applies various attention transformations on data. It needs a time-series of queries and a time-series of values to calculate the attention and the final linear transformation to obtain the output. This is a faster version of the general attention technique. It is similar to the `global attention` method described in [Effective Approaches to Attention-based Neural Machine Translation](https://arxiv.org/abs/1508.04025)

这一层对数据应用各种注意力转换。它需要一个查询的时间序列和一个值的时间序列来计算注意力和最终的线性变换来获得输出。这是一般注意力技巧的快速版本。它类似于在基于注意的神经机器翻译的有效方法中描述的全局注意方法

### Attention Wrapper <a name="atnwrapper"></a>
The idea of the implementation is based on the paper [Effective Approaches to Attention-based Neural Machine Translation](https://arxiv.org/abs/1508.04025). This layer can be wrapped around any `RNN` in `Keras`. It calculates for each time step of the `RNN` the attention vector between the previous output and all input steps. This way, a new attention-based input for the `RNN` is constructed. This input is finally fed into the `RNN`. This technique is similar to the `input-feeding` method described in the paper cited. The illustration below is taken from the paper cited above.

该思想的实现是基于本文提出的基于注意的神经机器翻译的有效方法。这一层可以围绕在Keras中的任何RNN。它为RNN的每个时间步长计算前一个输出和所有输入步长的注意向量。这样，就为RNN构造了一个新的基于注意力的输入。这个输入最后被输入到RNN。该技术与本文所述的输入-输入方法相似。下面的插图取自上面引用的论文。

<img src="https://i.imgur.com/AZKWSd2.png" height=300>
