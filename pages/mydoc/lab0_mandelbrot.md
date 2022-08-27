---
title: 实验0-曼德博集合
sidebar: mydoc_sidebar
permalink: lab0_mandelbrot.html
usemathjax: true
---

<iframe src="//player.bilibili.com/player.html?aid=50797775&bvid=BV1N441187Dh&cid=88938038&page=1"  scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%"> </iframe>

## 复数与复平面
我们把形如 $$z=a+bi$$（$$a$$、$$b$$均为实数）的数称为复数。

复平面（Complex plane）是用水平的实轴与垂直的虚轴建立起来的复数的几何表示。一个复数的实部用沿着 x 轴的位移表示，虚部用沿着 y 轴的位移表示。

数学中的复数的模。将复数的实部与虚部的平方和的正的平方根的值称为该复数的模。

$$|z|=\sqrt{a^2+b^2}$$

## 曼德博集合的其中一个定义

考虑这样一个函数：

$$f(z)=z^2+c$$

其中 $$z$$ 和 $$c$$ 都为虚数。

我们设 $$a_n=f(a_{n-1}), a_1=0$$

根据 $$c$$ 的不同，可能会有以下两种可能：
1. 任意自然数 $$k$$, 均有
   $$|a_k| \le 2$$
2. 存在自然数 $$k$$, 使得
    $$|a_k| \gt 2$$

所有第一种可能的 $$c$$ 构成了一个集合，就是曼德博集合。由于 $$c$$ 是复数，把集合内的点画在复平面上，就形成了图像。


## 补充视频
[什么是Mandelbrot Set?](https://www.bilibili.com/video/BV15W411b7LY)


## [Netpbm](https://en.wikipedia.org/wiki/Netpbm)

```
P3           # "P3" 代表这是一个用 ASCII 字符集描述 RGB 彩色图像的文件
3 2          # "3 2" 分别代表图片的宽和高
255          # "255" 是每个颜色的最大值（考虑到兼容性，这里最好保持 255）
# 这上面是头部描述
# 下面是描述像素颜色的三元组
255   0   0  # red
  0 255   0  # green
  0   0 255  # blue
255 255   0  # yellow
255 255 255  # white
  0   0   0  # black
```
这样虽然能描述一张图片，但是我们知道一个 ASCII 字符就要 1 个字节，描述一个像素就要 12 个字节，但实际上我们描述三个 0~255 的数字只需要 3 个字节。

于是我们可以把 P3 改成 P6, 下面的像素就直接打印 3 个字节，缺点是不能用文本编辑器查看和修改了。

## 所以到底怎么画？
如何编程判断一个点是否在曼德博集合内呢？算个 800 次！

如果这 800 次都满足条件那就认为它在集合内，我们上亮色（这样做更好看）。

如果在第 400 次模厂超过了 2, 那么就上稍微暗一点的色，如果只有 10 几次我们就上黑色。

于是我们可以定义一个数组：

```c
int x[W][H];
```
用来存放每个点“满足条件的次数”。

你的任务就是算出这个数组！

## 如何选点
实数是无穷的，而我们的数组是有限的。
你可以先使用[这个网站](https://mandel.gart.nz/)来寻找你想要的那个点 $$c$$，然后 `x[a][b]` 就对应着 $$(a*scale+c_x,b*scale+c_y)$$

## 准备 lab 环境

> - gcc
> - make
> - ffmpeg
> - git

```shell
git clone xxx
```

找到 `mb.c`，那将是你需要完成的程序。

在完成对应部分后，在 `mb.c` 的同级目录下，执行 `make`

生成的 `0001.ppm` 就是目标文件。

你可以指定缩放参数 `make scale=5e-8`

使用 `make clean` 来清除输出文件。

## 参考图像
> scale 为 8e-8, c=0.365724769+0.120668683i 时

## 彩蛋！
还记得我们第一节课上说的，视频就是连续的图像吗？

当你正确地实现了这个 lab 之后，我们特地为你准备了一份礼物！

```
make run scale=你的初始缩放 steps=总共的帧数 steplen=步长 -j10
```

这时候你的目录底下会有一个 `out.mp4`, 打开它，没错，这就是这次 lab 的成果！