# FPN

### FPN基本结构

FPN会使用CNN网络中每一层的信息来生成最后的表达特征组合。下图是它的基本架构。从中我们能看到FPN会模型每个CNN层的特征输出进行处理以生成反映此维度信息的特征。而自上至下处理后所生成出的特征之间也有个关联关系，即上层high level的特征会影响下一层次的low level特征表达。最终所有的特征一起用来作为下一步的目标检测或类别分析等任务的输入。

<image src="../image/FPN.png" weight="550" height="400" style="display:block; margin:0 auto;">

### FPN详细介绍

FPN是传统CNN网络对图片信息进行表达输出的一种增强。它目的是为了改进CNN网络的特征提取方式，从而可以使最终输出的特征更好地表示出输入图片各个维度的信息。它的基本过程有三个分别为：自下至上的通路即自下至上的不同维度特征生成；自上至下的通路即自上至下的特征补充增强；CNN网络层特征与最终输出的各维度特征之间的关联表达。

<image src="../image/FPN-Detail.png" weight="550" height="400" style="display:block; margin:0 auto;">

- 自下至上的通路（Bottom-top pathway）：是指的普通CNN特征自底至上逐层浓缩表达特征的一个过程。此过程很早即被认识到了即较底的层反映较浅层次的图片信息特征像边缘等；较高的层则反映较深层次的图片特征像物体轮廓、乃至类别等；
- 自上至下的通路（Top-bottome pathway）：上层的特征输出一般其feature map size比较小，但却能表示更大维度（同时也是更加high level）的图片信息。此类high level信息经实验证明能够对后续的目标检测、物体分类等任务发挥关键作用。因此我们在处理每一层信息时会参考上一层的high level信息做为其输入（这里只是在将上层feature map等比例放大后再与本层的feature maps做element wise相加）;
- CNN层特征与每一级别输出之间的表达关联：在这里作者实验表明使用1x1的Conv即可生成较好的输出特征，它可有效地降低中间层次的channels 数目。最终这些1x1的Convs使得我们输出不同维度的各个feature maps有着相同的channels数目（本文用到的Resnet-101主干网络中，各个层次特征的最终输出channels数目为256）

