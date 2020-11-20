# 卷积神经网络

1.链式法则计算：
$$
y=f(x),z=g(y),\frac{\partial z}{\partial x}=\frac{\partial z}{\partial y}\cdot\frac{\partial y}{\partial x}
$$
<br>
2.卷积核奇偶选择:奇数卷积核，奇数有利于原始数据对应。也可以选择偶数卷积核

3.上采样：输入图像经过卷积神经网络提取特征后，输出尺寸会变小，而将图像恢复到原来尺寸，实现小分辨率到大分辨率的映射操作叫上采样。上采样常见三种方法：双线性差值(bilinear)，反卷积(Transposed Convolution)，反池化(Unpooling)

4.反卷积是一种特殊的正向卷积，先按照一定的比例通过补0来扩大输入图像的尺寸，接着旋转卷积核，再进行正向卷积。反卷积只能恢复尺寸，不能回复数值。

5.ReLU:将负值数据置0

6.池化就是降维

7.全卷积结构(FCN):没有全连接层。特点：1.输入图片大小无限制2.空间信息有丢失3.参数更少，表达能力更强

8.全局部卷积连接的缺陷：

1. 预处理：大量对准，对对准要求高，原始信息可能丢失
2. 卷积参数数量大，模型收敛难度大，需要大量数据
3. 模型可扩展性3差，基本限于人脸计算

9.逆卷积：生成图片有更好的连贯性，有更好的空间表达能力

10.灰度化：在RGB模型中，如果R=G=B，则彩色表示一种灰度颜色，其中R=G=B的值叫做灰度值，因此灰度图像每个像素只需一个字节存放灰度值（又称强度值，亮度值），灰度范围为0-255

11.灰度化两种方法：

方法一

   灰度化后的R=（处理前的R + 处理前的G +处理前的B）/ 3

   灰度化后的G=（处理前的R + 处理前的G +处理前的B）/ 3

   灰度化后的B=（处理前的R + 处理前的G +处理前的B）/ 3

方法二

   灰度化后的R =  处理前的R * 0.3+ 处理前的G * 0.59 +处理前的B * 0.11

   灰度化后的G =  处理前的R * 0.3+ 处理前的G * 0.59 +处理前的B * 0.11

   灰度化后的B =  处理前的R * 0.3+ 处理前的G * 0.59 +处理前的B * 0.11

12.贝叶斯公式：P(A|B)=P(B|A)*P(A)/P(B)

13.IoU=A∩B/A∪B

14.如果导数为负，则参数向更大的方向走，反之，向更小的方向走。学习率控制变化速度

15.越复杂的model不一定会获得更好的结果，可能发生过拟合(overfit)

16.传统梯度下降：<br>
<image src="../image/Gradirnt-Descent.png" weight="550" height="400" style="display:block; margin:0 auto;">

17.动量梯度下降：<br>
<image src="../image/Momentum-Gradirnt-Descent.png" weight="550" height="400" style="display:block; margin:0 auto;">

18.Dropout:每次更新参数时都要随机丢掉一部分神经元，对新的神经网络进行训练。训练时准确率下降，但测试时会上升。测试时不dropout,但权重要乘以(1-p%)(p%是训练时设置的dropout rate)

19.RNN:将之前的输出存贮起来，下次使用后更新<br>
<image src="../image/RNN.png" weight="550" height="400" style="display:block; margin:0 auto;">

20.Elman NetWork&Jordan Network<br>
<image src="../image/Elman&Jordan.png" weight="550" height="400" style="display:block; margin:0 auto;">

21.Bidirectional RNN:看的范围比较广<br>
<image src="../image/Bidirectional-RNN.png" weight="550" height="400" style="display:block; margin:0 auto;">

22.LSTM:<br>
<image src="../image/LSTM.png" weight="550" height="400" style="display:block; margin:0 auto;">

23.RNN换为LSTM的原因：LSTM可以解决梯度消失的问题。<br>
<image src="../image/LSTM-inner.png" weight="550" height="400" style="display:block; margin:0 auto;">

24.CTC:用NULL代替重复符号

25.Self-Attention：<br>
<image src="../image/Self-Attention.png" weight="550" height="400" style="display:block; margin:0 auto;">

26.激活函数

激活函数分为：饱和激活函数和非饱和激活函数

1）饱和激活函数：能解决梯度消失问题，能加快收敛速度，如sigmod,tanh

2）非饱和激活函数：

**ReLu**

**ELUs**:指数线性单元，它试图将激活函数的平均值接近零，从而加快学习速度。还能通过正值标识来避免梯度消失

**Leaky ReLUs**:给所有负值赋予一个非零斜率

**PReLU**:Leaky ReLUs的变体。负值部分斜率是根据数据来定的，而非预先定义。

**RReLU**:Leaky ReLU的变体，训练中负值斜率随机，测试时固定

<image src="../image/RReLU.png" weight="550" height="200" style="display:block; margin:0 auto;">

下图是ReLU,Leaky ReLU,PReLU,RReLU的比较：

<image src="../image/relu-compare.png" weight="550" height="200" style="display:block; margin:0 auto;">



