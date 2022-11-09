---
title: Python利用Opencv实现视频字符化
date: 2022-01-18 23:53:26
tags:
---

## 一、安装Opencv

利用pip安装Opencv，在终端输入：

``` shell
pip install opencv-python
```

## 二、Opencv的基本操作

### 图片操作

1. 图片读取、预览

	``` python
	import cv2
	image = cv2.imread('image.jpg')	#读取JPG图片
	
	cv2.imshow('image', image)	#在窗口中显示图片
	cv2.waitKey(0)
	cv2.destroyAllWindows()	#关闭窗口
	```

2. 灰度转换

	``` python
	gray = cv2.cvtColor(frame, cv2.COLOR_RGB2GRAY)
	```

3. 更改图片大小

	``` python
	image_resize = cv2.resize(image, (100, 40))
	```

### 视频操作

1. 读取视频

``` python
video = cv2.VideoCapture('video.mp4')
```

2. 逐帧读取

``` python
ret, frame = video.read() #读取第一帧
while ret:
    operation() #执行你的操作
    ret, frame = video.read() #在进入下一次循环前读取下一帧
```

## 三、图片字符化

我们知道每个图片由像素组成，字符化的过程就是把每一个像素点替换成字符的过程，因此我们只需要将图片中的每一个像素点转换为相应点字符即可。Opencv根据颜色参数表，把灰度分为256分，代表不同的程度，因此我们只需要根据颜色表和我们的字符表建立一个映射关系。这里我们取字符表为

``` python
dic = ''' .'`^",:;Il!i><~+_-?][}{1)(|\/tfjrxnuvczXYUJCLQ0OZmwqpdbkhao*#MW&8%B@'''
```

由映射关系有：
$$
\frac{\text{颜色值}}{\text{颜色表长度}} = \frac{\text{字符在字符表中的位置}}{\text{字符表的长度}}
$$
即：
$$
\text{字符在字符表中的位置}=\frac{\text{颜色值}}{\text{颜色表长度}}\times \text{字符表的长度}
$$

### 图片字符化完整代码

``` python
import cv2

dic = ''' .'`^",:;Il!i><~+_-?][}{1)(|\/tfjrxnuvczXYUJCLQ0OZmwqpdbkhao*#MW&8%B@'''
image = cv2.imread('image')
gray = cv2.cvtColor(image, cv2.COLOR_RGB2GRAY)
gray = cv2.resize(gray, (100, 40)) #大小可自定义调节
str_image = ''

for line in gray:
    for pixel in line:
        index = int(pixel / 256 * len(dic)) #获取对应字符的下标
        str_image += dic[index]
    str_image += '\n' #每转换一行后要记得换行

print(str_image)
```

## 四、视频字符化

基于以上步骤，我们只需要逐帧读取视频，再逐帧字符化即可

### 视频字符化完整代码

``` python
import os
import cv2

dic = ''' .'`^",:;Il!i><~+_-?][}{1)(|\/tfjrxnuvczXYUJCLQ0OZmwqpdbkhao*#MW&8%B@'''

video = cv2.VideoCapture('video.mp4')
ret, frame = video.read()

while res:
    str_image = ''
    gray = cv2.cv2.cvtColor(frame, cv2.COLOR_RGB2GRAY)
    gray = cv2.resize(gray, (100, 40)) #将图片压缩以减少计算量
    
    for line in gray:
        for pixel in line:
            index = int(pixel / 256 * len(dic))
        str_image += '\n'
    os.system('clear') #清空屏幕，Windows为cls
    print(str_image)
    ret, frame = video.read()
```

### 附加（提高转换效率的一些办法）

利用numba提高计算速度

``` python
import numba as nb
```

利用sys禁用输出缓冲区

``` python
import sys
sys.stdout.flush() #替换os.system('clear')
```

#### 参考

- [1] [知乎]:https://zhuanlan.zhihu.com/p/129622984

