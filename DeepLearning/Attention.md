# Attention机制

### Encoder-Decoder框架

<image src="../image/Encoder-Decoder.png" weight="550" height="400" style="display:block; margin:0 auto;">

Encoder-Decoder框架是将输入的句子进行非线性变换变成中间语义C,再由解码器利用中间语义和历史信息生成目标语句

Encoder-Decoder没有注意力模块所以每次参与解码的中间语义信息均相同
$$
y_1 = f(C)\\
y_2 = f(C,y_1)\\
y_3 = f(C,y_1,y_2)\\
...
$$

### Soft Attention

Attention机制则根据其影响程度给每个单词一个概率，即该单词的注意力大小，如 Tom chase Jerry

```
(Tom,0.3)(Chase,0.2)(Jerry,0.5)
```

<image src="../image/Attention-01.png" weight="550" height="400" style="display:block; margin:0 auto;">

解码器对不同的输入单词采用不同的中间语义信息解码
$$
y_1 = f(C1)\\
y_2 = f(C2,y_1)\\
y_3 = f(C3,y_1,y_2)\\
...
$$
<image src="../image/Attention-02.png" weight="550" height="400" style="display:block; margin:0 auto;">

### Self Attention

<image src="../image/Self-Attention-01.png" weight="550" height="400" style="display:block; margin:0 auto;">

首先计算Q和K之间的点乘，其意义为句中每每两词的相关度。为防止其过大会除以一个尺度标量
$$
\sqrt{d_k}，d_k为为一个query和key向量的维度
$$
再利用softmax归一化为概率分布，再乘以矩阵V就得到权重求和表示，公式
$$
Attention(Q,K,V) = softmax(\frac{QK^t}{\sqrt{d_k}})V
$$
