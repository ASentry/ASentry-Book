# 函数笔记

transforms.ToTensor() 将numpy的ndarray或PIL.Image读的图片转换成形状为(C,H, W)的Tensor格式，且/255归一化到[0,1.0]之间

math.floor()向下取整

filter() 函数用于过滤序列，过滤掉不符合条件的元素，返回由符合条件元素组成的新列表。<br>
该接收两个参数，第一个为函数，第二个为序列，序列的每个元素作为参数传递给函数进行判断，<br>
然后返回 True 或 False，最后将返回 True 的元素放到新列表中<br>

zip() 函数用于将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的列表。<br>
如果各个迭代器的元素个数不一致，则返回列表长度与最短的对象相同，利用 * 号操作符，可以将元组解压为列表<br>

Math.ceil() “向上取整”， 即小数部分直接舍去，并向正数部分进1

resize(size, interpolation=2)   pytorch函数，图像与处理有两个参数一个是大小H*W,interpolation插值有四种Image.BICUBIC，PIL.Image.LANCZOS，PIL.Image.BILINEAR，PIL.Image.NEAREST

torch.cat()是将两个张量（tensor）拼接在一起

unsqueeze()添加维度，squeeze()删除维度

