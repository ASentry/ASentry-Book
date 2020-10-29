# CTC,RNN-T

### CTC

CTC全称Connectionist Temporal Classification,主要是为了解决利用RNN训练时需要目标label与输入的每一帧需要alignment的问题，即我们需要知道哪几帧输入对应输出的哪个字符并且知道如何分割不同输出字符对应的输入帧的边界，而且有的时候这种边界较为模糊，这种需要逐帧对应的标记的数据相较于只是需要简单的文字输出的人力要求要高很多。

为了解决alignment的问题，CTC定义了blank symbol来做填充，假定填充符号为—，如果我们输入的音频有八帧，而对应label为cat只有三个字符则，CTC可以做如下填充
$$
输入语音为\vec{x}=x_1x_2\cdot\cdot\cdot x_n对应label为\vec{y}=y_1y_2\cdot\cdot\cdot y_n\\
cc-aa-t-\\
c-aa-tt-\\
c-aaa-t-\\
...\\
\sum_{\hat{y}\in B(\vec{y},\vec{x})}P(\hat{y},\vec{x})=\sum_{\hat{y}\in B(\vec{y},\vec{x})}\Pi_{t=1}^T P(\hat{y_t},\vec{x})
$$
该模型可用下图表示：

<image src="../image/CTC.png" weight="550" height="400" style="display:block; margin:0 auto;">

### RNN-T

RNN-T全称是Recurrent Neural Network Transducer，是在CTC的基础上改进的。CTC的缺点是它没有考虑输出之间的dependency，即之后的帧和之前的帧没有任何关联，而RNN-T则在CTC模型的Encoder基础上，又加入了将之前的输出作为输入的一个RNN，称为Prediction Network，再将其输出的隐藏向量与encoder得到的放到一个joint network中，得到输出logit再将其传到softmax layer得到对应的class的概率。

结构如下：

<image src="../image/RNN-T.png" weight="550" height="400" style="display:block; margin:0 auto;">