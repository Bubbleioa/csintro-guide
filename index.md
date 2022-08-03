---
title: "计算机科学技术导论 课程网站 2022"
keywords: computer homepage
sidebar: mydoc_sidebar
permalink: index.html
---
{% include note.html content="如果本文档访问速度较慢或者不稳定，你可以把这个仓库克隆到本地，然后离线查看本文档。但是请注意，如果选择了此方式，你需要留意来更新此文档的内容。" %}

## 关于本课程

> 人类的天性就是不断地推动自己越过新的边界，我们考验自身的极限，我们直面自己的恐惧，我们奋起迎接挑战，最终成为超越我们自身的存在，一个文明。 ——《文明6》开场CG

虽然想说“我们就是通过计算机不断超越自己而形成了超越我们自身的文明”，但是这样的说法有点自视甚高，并且太将这门学科神化了。

但事实是我们如今周围的一切都离不开计算机。

1. 用到了计算机，结果也在计算机中呈现。
  - 计算机科学
  - 传媒
  - 游戏
  - ...

2. 用到了计算机，结果产出后脱离计算机。
  - 土木工程
  - 几乎一切的产品设计、生产
  - ...

3. 使用计算机进行辅助。
  - 运动员训练
  - 疫情防控
  - ...

4. 没有用到计算机，但是要拿计算机举例子。
  - ...

因此大部分人都能在计算机科学中找到属于自己的那份热爱，但有很多大学生在计算机专业中仍然感到迷茫和乏味，这就是这门课开设的目的——想要帮助大家找到属于自己的热情和提供一条学习计算机科学的道路。

计算机科学是一门**人造科学**，这意味着在计算机科学中，不是我们去研究如何去如何解释描述计算机，而是我们定义了计算机上的一切。

如果你是喜欢刨根问底的同学，那么恭喜你，计算机科学就是这样的一门学科。在计算机世界中，无论一个什么样的现象，你都能追问到它最本质的产生原因——这也就意味着，我们就是计算机世界中的“神”。
如果这些还没能使你热血沸腾，跃跃欲试的话，不如先来**剧透**一下这门课我们的成果：
1. 通过非常简短的代码和浅显的数学知识画出这样的图！（你会发现每个人每次访问下面的图片都不同）
<img id="mb" src=""/>
2. 游戏修改器！我们将自己手写一个游戏修改器，在游戏里所向披靡。
3. 一个比这个网站还要“厉害”的网站！
4. 《原神》《LOL》《CS:GO》《冰雪奇缘》我们并不能做出这些……但是能做出它们背后的最小的渲染器！
5. 通过自己的写的 UDP 协议，与其他人来一场酣畅淋漓的[屏风式四子棋](https://zh.wikipedia.org/zh-hk/%E5%BA%8F%E8%B4%AF%E5%8D%9A%E5%BC%88)对战！

<script>
  // 使用 api 渲染图片，兼容不支持 WASM 的浏览器
  function randomInRange(min, max) {
    return Math.random()<0.5? ((1-Math.random()) * (max-min) + min) : (Math.random() * (max - min) + min)
  }
  const mb = document.getElementById('mb')
 
  mb.setAttribute('src','https://service-avb1tv8k-1303953543.hk.apigw.tencentcs.com/release/image?scale='+randomInRange(9e-9,1.5e-7)+'&id=2')
</script>
{% include note.html content="如果你是通过网课形式上这门课并且英语水平还不错的话，推荐直接观看 <a href='https://cs50.harvard.edu/'>CS50</a>，富有激情的主讲 David J. Malan 以及他背后的整个课程团队提供了世界上最顶尖的大学课程。" %}

## 外部资料

本课程主要是受 [CS50](https://cs50.harvard.edu/) 和 [nju-ics](https://nju-projectn.github.io/ics-pa-gitbook/ics2022/) [nju-os](http://jyywiki.cn/OS/2022/) 启发，本课程最大的任务之一就是为大家扫清通过网课上这些课程的障碍。

### 获取帮助

[nju-ics-pa](https://nju-projectn.github.io/ics-pa-gitbook/ics2022/#%E5%A6%82%E4%BD%95%E8%8E%B7%E5%BE%97%E5%B8%AE%E5%8A%A9)

## 学术诚信

[什么是学术诚信](http://integrity.mit.edu/)

在这门课上你需要做到以下几点：
1. 不公开自己的代码。这会使得你的学弟学妹缺少应有的锻炼。
2. 不抄袭别人的代码。
3. 不和同学讨论代码层面的`细节`。

尤其是在这门没有学分的课上，完全没有违反学术诚信的理由。如果需要寻求帮助的话，可以在 Office Hour 或者找完成了的同学询问在哪里能找到相关信息。

{% include tip.html content="例如你不清楚如何去输入一个无符号整数，正确的做法是询问：“我该在哪里知道怎么输入所有类型的变量？”，你可能被告知使用 <code class='language-plaintext highlighter-rouge'>man scanf</code> 来获取帮助，你会在 Conversions 这一项中找到你想要的结果，并且你还会意外地发现这个百分号开头的东西叫做 type modifier characters" %}

{% include warning.html content="如果老师会认真地查看你的代码的话，违反学术诚信还是一种对于劳动者的不尊重，" %}

## 课程环境

1. 最低要求
  - CPU架构: any
  - 操作系统: any
  - 其他: 需要能使用 chromium 内核的浏览器（或者 Firefox）
  - 例如: 手机，树莓派，平板
  - 说明: 可能无法顺利完成部分 Lab
2. 最佳配置
  - CPU架构: x64
  - 操作系统: Windows with wsl/MacOS/Linux(gui)
  - 说明: 如果你选择了 MacOS 的话，游戏修改器的 Lab 可能需要自己准备游戏并且更改系统调用。

课程环境的获取和配置可以前往`扇区0`了解详情。