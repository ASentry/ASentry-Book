# 图像预处理-增强

图像增强可分为两类：

- 频域法
- 空间域法

频域法，顾名思义，频域法就是把图像从空域利用傅立叶、小波变换等算法把图像从空间域转化成频域，也就是把图像矩阵转化成二维信号，进而使用高通滤波或低通滤波器对信号进行过滤。采用低通滤波器（即只让低频信号通过）法，可去掉图中的噪声；采用高通滤波法，则可增强边缘等高频信号，使模糊的图片变得清晰。<br>

其次，介绍一下空域方法，空域方法用的比较多，空域方法主要包括以下几种常用的算法：

- 直方图均衡化
- 滤波

### 滤波 ###

基于滤波的算法主要包括以下几种：

- 均值滤波
- 中值滤波
- 高斯滤波

### 代码： ###

```
import cv2
# 读取图像并转化为灰度图
img = cv2.imread("/Opencvproject/img2007/2007_000793.jpg")
gray=cv2.cvtColor(img,cv2.COLOR_RGB2GRAY)
cv2.imshow("gray", gray)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

<image src="../image/Gray.png" weight="550" height="400" style="display:block; margin:0 auto;">

```
# 显示灰度直方图
# opencv calcHist函数传入5个参数：
# images：图像
# channels：通道
# mask：图像掩码，可以填写None
# hisSize：灰度数目
# ranges：回复分布区间
def histogram(gray):
    hist = cv2.calcHist([gray], [0], None, [256], [0.0, 255.0])
    plt.plot(range(len(hist)), hist)
    plt.show()
histogram(gray)
```

<image src="../image/Histogram-Gray.png" weight="550" height="400" style="display:block; margin:0 auto;">

```
# 直方图均衡化
dst = cv2.equalizeHist(gray)
histogram(dst)
```
<image src="../image/Histogram-Equalize.png" weight="550" height="400" style="display:block; margin:0 auto;">

<image src="../image/Equalize-Gray.png" weight="550" height="400" style="display:block; margin:0 auto;">