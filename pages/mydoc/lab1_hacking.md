---
title: 实验1-游戏修改器
sidebar: mydoc_sidebar
permalink: lab1_hacking.html
usemathjax: true
---

<link href="./css/chessboard.css" rel="stylesheet">

> 受 [NJU-OS](http://jyywiki.cn/OS/2022/) 启发

{% include callout.html content="想要戒掉单机游戏，最好的方法就是作弊。" type="info" %}

为了防止大家沉迷游戏，我们特地为大家准备了这样一个实验：游戏修改器（雾）

{% include warning.html content="对专有软件进行二进制破解并分发可能涉及法律问题，包括但不限于多人在线游戏的外挂，云盘不限速下载客户端等，本实验请仅作为学习使用。" %}

# hacking 原理

[source](https://github.com/moroshko/chessboard)
<div id="board"></div>

<script src="./js/chess.js"></script>
<script src="./js/chessboard.js"></script>
<script src="./js/app.js"></script>

先来挑战下国际象棋！

国际象棋中的状态比较好表示（不是最优解）：

```c
struct node{
    int x,y;
    int type;
}chess[32];
```

那既然游戏也是程序，程序把变量存放在内存中，那我们修改游戏的内存，不就可以修改游戏的一切了吗？（实际上不只是游戏，任意的程序都可以。）

但是我们并不知道游戏的变量存放在内存中的哪个位置，甚至就算把游戏源代码给你，你都不知道该改哪里才能让你变成“亿万富翁”。

变量在游戏某一局中的位置不会改变，这意味着我们可以将我们想修改的位置筛选出来！

于是我们可以在第一次全局扫描内存的时候找到我们想要的值的位置，记录下来

例如我们现在的金钱数是 `0x25` 

```
0    1    2    3
0x35 0x25 0x41 0x25
```

经过一次扫描后，我们记录下 1 和 3 号位置。

在游戏中我们花掉一点钱，现在只剩下 `0x20` 了

```
0     1    2     3
不重要 0x20 不重要 0x30
```

于是我们就锁定了，是 1 号位置存放我们的金钱！

这个时候我们把 1 号位置修改成我们想要的值就可以了。

这里的 x 号位置可以按字节编址，也可以按照 4 个字节（一个 int）

# 具体实现

为了保证高效和安全，如今操作系统的进程内存非常复杂，我们在其上面进行了一次抽象。

具体来说，内存就是一个`char *mem`，主要通过下面两个接口完成实验：

1. ```c
unsigned char *fetch_mem(uint64_t ch_addr, int length, int *read_btyes, bool is_first_scan);
// ch_addr 为数组下标， length 为要读取多少个字节，read_btyes 作为函数的“第二个返回值”，返回的是成功读取的字节数，一般来说 read_btyes == length
// is_first_scan 如果是首次全局扫描为 true, 否则为 false, 用来减少系统调用，加速扫描
// 返回值为 mem + ch_addr
```
`x = mem[i...i+length]` => `x = fetch_mem(i, length)`

2. ```c
void write_mem(uint64_t ch_addr, unsigned char *ch, int length);
// ch_addr 与 length 同上
// ch 为要写入的数据，注意我们的环境是小端机
```

还有一个初始化环境，需要在扫描之前调用：

```c
int init(char *process_name);
// 传入要 hacking 的进程名
```

祝你成功戒掉游戏！