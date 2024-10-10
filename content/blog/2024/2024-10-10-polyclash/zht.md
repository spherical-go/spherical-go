+++

title = "polyclash：第一個對弈程序 "
description = "我們已經開發了一個簡單的球面圍棋程序 polyclash，在這裡我們簡單介紹 polyclash 的情況和如何使用的方法。"
draft = false

[taxonomies]
tags = ["繁體中文"]

[extra]
feature_image = "example.png"
feature = true
+++

根據前文的想法，我們已經開發了一個簡單的球面圍棋程序 polyclash，在這裡我們簡單介紹 polyclash 的情況和如何使用的方法。

polyclash 是球面圍棋的一個參考實現，基於 Python 語言開發，代碼完全是[開源](https://github.com/spherical-go/polyclash)的。

polyclash 包含 client 和 server 兩個程序，可以支持本機對弈、局域網對弈和互聯網對弈。任何人都可以搭建、運行自己的 server，只要連接到服務器上，就可以下棋。

對於本地對弈還引進了一個非常笨拙的 AI 選手。互聯網服務器的搭建，我們在本文暫且不論，只告訴大家使用的方法。

### 安裝與啟動

因為程序使用 Python 語言開發，所以我們需要 Python 語言 3.10 以上的運行環境支持。安裝非常簡易，只需要執行下述命令

```
pip install polyclash
```

就可以安裝獲得 `polyclash-client` 和 `polyclash-server` 兩個本地的運行命令。

執行如下命令，可以啟動客戶端

```
polyclash-client
```

執行如下命令，可以啟動服務器

```
polyclash-server
```


### 遊戲界面

整個遊戲的界面分成 4 個部分：

{{img(path='/blog/2024/2024-10-10-polyclash/example.png', width=1238, height=350, op="fit_height")}}

* 對弈區：對弈區是下棋的盤面所在，可以通過鼠標旋轉定位到球面的某個區域，然後點擊棋盤格點放置棋子。
* 概覽區：是對全球的四個大陸與海洋區域提供的全球概覽，可以看到黑白子的全球分佈。
* 指示區：指示目前是黑方還是白方的輪次，也提供黑白雙方各自佔有的面積。
* 坐標軸：指示球面旋轉中的方位。

### 對弈

整個遊戲的缺省設置是本地的人機對弈，但是由於 AI 的設計比較簡單，可能並沒有非常強烈的對抗感。

菜單的本地模式里允許本地的人人對弈，但是由於版本演進里有一個 bug，這個功能目前受限。

我們重點介紹的還是網絡對弈。

第一步是通過菜單“網絡模式”的“創建”項目來開啟一次對弈。

{{img(path='/blog/2024/2024-10-10-polyclash/create-network-game.png', width=1238, height=350, op="fit_height")}}

第二步：我們需要在對話框填入網絡服務器，可以使用參考服務器 “ https://sphericalgo.org ”

第三步：打開服務器網址“GOSERVER/sphgo/”，如我們參考服務器，就是打開網址“ https://sphericalgo.org/sphgo/ ”，在這個頁面我們可以獲取到服務器的 token

{{img(path='/blog/2024/2024-10-10-polyclash/server-token.png', width=1238, height=150, op="fit_height")}}

第四步：在對話框填入服務器 token，點擊 “Connect”，會從服務器獲得分配的遊戲房間的黑方、白方和觀眾的密碼，然後通過聊天工具把黑方、白方的密碼告訴對弈的選手

第五步：點擊菜單里“網絡模式”的“加入”項目來加入遊戲，在加入過程里，黑方、白方需要輸入各自的密碼，然後各自點擊“Ready”，等雙方都就緒后遊戲自動開啟。

{{img(path='/blog/2024/2024-10-10-polyclash/join-network-game.png', width=1238, height=350, op="fit_height")}}

儘管需要五步，略微有點複雜，但這已經是我們能想到的最簡單的處理方式了，畢竟我們需要支持多個服務器都可以選擇的情況。