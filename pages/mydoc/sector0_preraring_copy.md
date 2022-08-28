---
title: 环境准备-扇区0
sidebar: mydoc_sidebar
permalink: sector0_preparing_copy.html
---

{% include callout.html content="环境准备是指通过在你的电脑上安装一些软件、执行某些操作，使得你的电脑可以非常舒适地进行某项学习/工作的过程。所谓工欲善其事，必先利其器就是这个道理。<br/>本课程采用渐进式的环境配置，在对应的课程会有对应的文档，请在课前完成。" type="info" %} 


## GitHub 注册

GitHub 是如今世界上最大的代码托管仓库和开源社区，在今后的学习过程中，你将逐渐意识到它的优点。

{% include warning.html content="还愣着干什么？你已经开始了本课程的第一个“作业”，赶紧去完成它吧！注册一个网站的帐号对你来说应该不是难事，全英文的网站可能是唯一的障碍，你将在之后的学习过程中碰到更多的，不可机翻的英文资料，大部分的问题用英文能更快地获得更准确的答案，所以不要用翻译软件，凭着自己的积累完成这第一个任务吧！" %}
## 选择你的角色

本课程原则上不会限定大家使用的机器，无论你是 Windows、Linux 还是 MacOS，但考虑到大部分人的使用情况，只对 Linux 和 Windows 做环境配置的说明。


### Windows

首先下载 [LATEST UCRT runtime Win64](https://winlibs.com/)
{% include tip.html content="诶？为什么下载速度这么慢呢？可能某些同学压根没法访问。上网搜搜，或者向同学请教一下，你会获得在知识的海洋里遨游的门票。" %}
==TODO:环境变量配置==

下载并安装 [VScode](https://code.visualstudio.com/)

#### 安装 WSL（可选/推荐）
{% include warning.html content="即便你选择安装 WSL,还是要先完成上述 Windows 环境配置，这和我们后续实验内容有关。" %}
WSL 全称 Windows Subsystem for Linux，可以在 Windows 上运行 Linux（没错，就是一个虚拟机），我们强烈建议你使用 Linux 来学习计算机。
==TODO:WSL==

安装完 WSL 之后，剩下的环境配置都可以参照 Linux 

### Linux
根据你的发行版不同，命令会有些许不同。

安装 [VScode](https://code.visualstudio.com/docs/setup/linux)
#### Ubuntu
安装编译器和手册：
```shell
sudo apt update
sudo apt install build-essential
sudo apt-get install manpages-dev
```
你可以使用如下命令来检查安装是否成功：
```shell
gcc --version
```
#### CentOS7
安装编译器和手册：
```
sudo yum group install "Development Tools"
sudo yum install man-pages
```
你可以使用如下命令来检查安装是否成功：
```shell
gcc --version
```
### MacOS 以及其他环境
如果你真的需要这部分的文档来帮助，说明你已经是一名十足的 Geek 了，所以你只要在你对应的平台上装上：
1. 文本编辑器
2. C 语言编译器
相信这难不倒你。

### 通用解决方案
为了防止有人说：“我只有一个安卓平板，你是不是看不起我的安卓平板？”之类的话，我们特地准备了兜底的方案，如果：
1. 环境配不好
2. 设备太特殊

那么你的设备只需要一个浏览器，就能进行我们的这门课程。
==TODO:GitPod==