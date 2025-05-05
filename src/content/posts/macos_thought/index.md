---
title: Ｗindows老狗的MacBook使用心得
published: 2025-05-05
description: "最近換了MacBook OwO"
tags: ["life"]
category: life
draft: false
lang: zh_TW
---

# 前言
這篇是給電機/電子/資訊/工程相關學生寫的

如果您是已就業人士，請看看就好

另外，我也並非專業的用戶，僅發表個人的想法而已

# 我與windows
我是大概小二開始接觸電腦的，那時候使用的是windows，就只是拿來看Youtube的

大概小五的時候，網路卡壞了，沒辦法幹嘛，就開始玩一些windows 7自帶的功能，那時候把控制台的各個設定都玩過一遍了XDD

那台應該是第4代intel i7，且有32GB RAM，在以前算是很高規格的

等到大概國二，開始喜歡打遊戲，也接觸了一些電腦硬體的知識，就求老爸買零件讓我組電腦

規格如下:
```
CPU: AMD R5-5600X
Motherboard: GIGABYTE B550M DS3H
RAM: 64GB
GPU: RTX 3060
ROM: 512GB + 1TB + 2TB
```

高中開始接觸資訊/軟體相關的，開始接觸linux系統 (Ubuntu/kali/EndeavourOS...)

高一的時候我爸買了一台windows平板(Microsoft Surface pro 9)，那時候全靠那台學競技程式

這台的缺點:
- 續航極差，x86還是不要做平板比較好
- 嚴重過熱，x86真的拜託不要做平板

之後我爸買了一台Dell XPS 15 9530要買給自己用，但他發現太重了，就拿給我用，我拿他學了kotlin還有CTF

規格如下:
```
CPU: intel i7-13700H
RAM: 32GB
GPU: intel Xe Grapgics + RTX-4050
ROM: 1TB
```

這台照樣有缺點:
- 重達1.9kg，加個電子學課本還有其他東西，書包日常超過3kg，對我這種每天花快兩小時在通勤的極不友好
- 耗電量大，平常基本要禁用4050
- 系統極不穩定，很常待機就莫名其妙過熱。且CPU大小核調度也很有問題，很常遇到待機某幾核飆到100%

是的，到此為止我都是用windows系統(XP/7/8/10/11 都使用過)

噢對了，另外推薦Windows 11 IoT Enterprise LTSC，非常穩定，桌機灌他到目前為止還沒遇到過什麼大問題

# 我與iOS

我在國中時使用的手機是iPhone SE 2，之後就改用google pixel了

## 歧視蘋果
大概國二開始，我覺得蘋果產品限制較多，給人的感覺冷冰冰的

在自訂性與可玩性方面，Android 明顯更加豐富

並且也覺得，Mac就是盤子在買的，就只是拿來在星巴克裝逼用

## 理解蘋果
之後看到M系列處理器有極高的能耗比，開始聊解蘋果產品

## 使用蘋果
MacBook Air M4比歷代價錢還低，且性價比很高，就想說順便換了

買的是24GB RAM + 256GB ROM版本


### 使用心得

目前使用下來，一個字：讚

我平常的使用非常高壓，還會開著windows虛擬機
![](https://i.ibb.co/0jfPqqRX/Clean-Shot-2025-05-05-at-14-33-43-2x.png)

在這種情況下，離電還是有不錯的順暢度，且開著省電要一整天應該是沒啥問題

不過因為我還是需要x86 linux/windows開發環境，所以會遠端remote回家

這邊推薦Parsec，他是P2P的連接方式，非常流暢

連學校網路的話，用Clouflare WARP就可以了

另外推薦虛擬機軟體Parallels，優點可以看這部影片
<iframe width="560" height="315" src="https://www.youtube.com/embed/nq0y7Ecjyx8?si=hdT-ImMmR1u_5bZ0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

~~破解版請自行尋找~~

其他就沒什麼要注意的了，macOS學習起來不會太困難

# 建議
網路上很多影片都是根據"Youtuber自身"為出發點，很少人以"學習開發的學生"為考量

不過，這邊就單純以電機/電子/資訊/工程相關學生為考量

首先，如果你沒有windows電腦，那我建議先買windows比較好

像是學習電子的學生，TINA-TI只能在windows上跑，我有用過macOS的電路模擬軟體，都不如TINA-TI強大

如果是電機或工程的學生，很大機率會碰到Autodesk的軟體，其大部分都只支援windows

- 建築、工程與營造產品
![CleanShot 2025-05-05 at 14.54.07@2x](https://hackmd.io/_uploads/Bk4sxJLxxe.png)

- 設計與製造
![CleanShot 2025-05-05 at 14.54.42@2x](https://hackmd.io/_uploads/Hy4axy8ell.png)

最後是軟體資訊相關，很多人看到Youtube那些"軟體工程師日常"都是拿著MacBook和一杯咖啡悠悠哉哉

如果是行動應用開發/網頁設計領域，使用Mac確實是個不錯的選擇

但，你是學生

你能確定你以後是做這個嗎？

況且，很多大學應該都有一門課叫"作業系統開發"或"軟體開發"

書上應該都是以x86架構系統作為範例

綜上，我建議**先有Windows再考慮Mac**

## 如何考慮Mac

MacBook Pro 雖然性能更強（有額外散熱、更多核心、更高 GPU 性能），但價格也明顯提高

若你不是經常做影像剪輯、高效能渲染、深度學習或重度虛擬化，則沒必要花更多成本去購買Pro系列

另外關於RAM/ROM的考慮，我是想說RAM無法擴充，把7000塊花在這搞不好比較值，畢竟ROM能用外接硬碟的方式擴充

不過，我最推薦的是16+256的版本，因為macOS的記憶體管理很優秀，不是很重度使用的話，16GB RAM應該是夠用

不過因為Mac後續沒辦法升級，建議多花些時間考慮