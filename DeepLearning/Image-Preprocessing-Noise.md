# 图像预处理-噪声

噪声主要分为以下几类：

- 椒盐噪声<br>
- 加性噪声<br>
- 乘性噪声<br>
- 高斯噪声<br>

图像去噪的方法有很多种，其中均值滤波、中值滤波等比较基础且成熟，还有一些基于数学中偏微分方程的去噪方法，此外，还有基于频域的小波去噪方法。均值滤波、中值滤波这些基础的去噪算法以其快速、稳定等特性，在项目中非常受欢迎，在很多成熟的软件或者工具包中也集成了这些算法。<br>

代码：<br>

```
import cv2
import numpy as np
import skimage
from skimage.util.dtype import convert

# 读取图像
img = cv2.imread("/Opencvproject/img2007/2007_001458.jpg")


# cv2.imshow("origin_img", img)
# cv2.waitKey(0)
# cv2.destroyAllWindows()

# #添加噪声
#1.利用第三方工具添加噪声
noise_img = skimage.util.random_noise(img,mode="gaussian")
# cv2.imshow("origin1_img", noise_img)
# cv2.waitKey()

# #2.自己生成噪声
# def add_noise(img):
#     img = np.multiply(img, 1. / 255, dtype=np.float64)
#     mean, var = 0, 0.01
#     noise = np.random.normal(mean, var ** 0.5, img.shape)
#     img = convert(img, np.floating)
#     out = img + noise
#     return out
#
#
# noise_img = add_noise(img)
# gray_img = cv2.cvtColor(noise_img, cv2.COLOR_BGR2GRAY)
# cv2.imwrite("D:/Opencvproject/img2007/handnoise.jpg", noise_img)

# 3.图像去噪
# 方法1：用第三方工具去噪
# denoise = cv2.medianBlur(img, ksize=3)
# denoise = cv2.fastNlMeansDenoising(img, ksize=3)
# denoise = cv2.GaussianBlur(img, ksize=3)

# def compute_pixel_value(img, i, j, ksize, channel):
#     h_begin = max(0, i - ksize // 2)
#     h_end = min(img.shape[0], i + ksize // 2)
#     w_begin = max(0, j - ksize // 2)
#     w_end = min(img.shape[1], j + ksize // 2)
#     return np.median(img[h_begin:h_end, w_begin:w_end, channel])
# 
# def denoise(img, ksize):
#     output = np.zeros(img.shape)
#     for i in range(img.shape[0]):
#         for j in range(img.shape[1]):
#             output[i, j, 0] = compute_pixel_value(img, i, j, ksize, 0)
#             output[i, j, 1] = compute_pixel_value(img, i, j, ksize, 1)
#             output[i, j, 2] = compute_pixel_value(img, i, j, ksize, 2)
#     return output
# 
# output = denoise(noise_img, 3)
# cv2.imshow("denoise_img", output)
# cv2.waitKey(0)
# cv2.destroyAllWindows()

```
