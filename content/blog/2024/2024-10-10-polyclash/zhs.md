+++
title = "polyclash：第一个对弈程序 "
description = "我们已经开发了一个简单的球面围棋程序 polyclash，在这里我们简单介绍 polyclash 的情况和如何使用的方法。"
draft = false

[taxonomies]
tags = ["简体中文"]

[extra]
feature_image = "example.png"
feature = true
+++

根据前文的想法，我们已经开发了一个简单的球面围棋程序 polyclash，在这里我们简单介绍 polyclash 的情况和如何使用的方法。

polyclash 是球面围棋的一个参考实现，基于 Python 语言开发，代码完全是[开源](https://github.com/spherical-go/polyclash)的。
polyclash 包含 client 和 server 两个程序，可以支持本机对弈、局域网对弈和互联网对弈。任何人都可以搭建、运行自己的 server，只要连接到服务器上，就可以下棋。
对于本地对弈还引进了一个非常笨拙的 AI 选手。互联网服务器的搭建，我们在本文暂且不论，只告诉大家使用的方法。

### 安装与启动

因为程序使用 Python 语言开发，所以我们需要 Python 语言 3.10 以上的运行环境支持。安装非常简易，只需要执行下述命令

```
pip install polyclash
```

就可以安装获得 `polyclash-client` 和 `polyclash-server` 两个本地的运行命令。

执行如下命令，可以启动客户端

```
polyclash-client
```

执行如下命令，可以启动服务器

```
polyclash-server
```

### 游戏界面

整个游戏的界面分成 4 个部分

{{img(path='/blog/2024/2024-10-10-polyclash/example.png', width=1238, height=350, op="fit_height")}}

* 对弈区：对弈区是下棋的盘面所在，可以通过鼠标旋转定位到球面的某个区域，然后点击棋盘格点放置棋子。
* 概览区：是对全球的四个大陆与海洋区域提供的全球概览，可以看到黑白子的全球分布。
* 指示区：指示目前是黑方还是白方的轮次，也提供黑白双方各自占有的面积。
* 坐标轴：指示球面旋转中的方位。

### 对弈

整个游戏的缺省设置是本地的人机对弈，但是由于 AI 的设计比较简单，可能并没有非常强烈的对抗感。

菜单的本地模式里允许本地的人人对弈，但是由于版本演进里有一个 bug，这个功能目前受限。

我们重点介绍的还是网络对弈。

第一步是通过菜单“网络模式”的“创建”项目来开启一次对弈。

{{img(path='/blog/2024/2024-10-10-polyclash/create-network-game.png', width=1238, height=350, op="fit_height")}}

第二步：我们需要在对话框填入网络服务器，可以使用参考服务器 “ https://sphericalgo.org ”

第三步：打开服务器网址“GOSERVER/sphgo/”，如我们参考服务器，就是打开网址“ https://sphericalgo.org/sphgo/ ”，在这个页面我们可以获取到服务器的 token

{{img(path='/blog/2024/2024-10-10-polyclash/server-token.png', width=1238, height=150, op="fit_height")}}

第四步：在对话框填入服务器 token，点击 “Connect”，会从服务器获得分配的游戏房间的黑方、白方和观众的密码，然后通过聊天工具把黑方、白方的密码告诉对弈的选手

第五步：点击菜单里“网络模式”的“加入”项目来加入游戏，在加入过程里，黑方、白方需要输入各自的密码，然后各自点击“Ready”，等双方都就绪后游戏自动开启。

{{img(path='/blog/2024/2024-10-10-polyclash/join-network-game.png', width=1238, height=350, op="fit_height")}}

尽管需要五步，略微有点复杂，但这已经是我们能想到的最简单的处理方式了，毕竟我们需要支持多个服务器都可以选择的情况。

