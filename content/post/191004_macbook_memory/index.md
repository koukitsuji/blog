---
title: "MacBook Pro Mid 2012のメモリを16GBへ増設"
date: 2019-10-04T19:15:14+09:00
update: 2020-06-30T19:15:14+09:00
slug: macbook-memory
draft: false

# post thumb
image: "1.jpg"

# meta description
description: "メモリを自力で16GBへ増設し、総額1.7万円でMacBook Pro Mid 2012を使用可能なマシンへ復活させた方法です。"

# taxonomies
categories:
  - "Programming"
tags:
  - "MacBook"

# post type
type: "post"
---

# はじめに

大学時代に買った``MacBook Pro Mid 2012 (13-inch)``ですが、さすがに動作が重くて使っていませんでした。

最近、iOSアプリ開発の欲が高まり、よっしゃ新しいMac買うかのぉと調べると、…高いッ！。型落ちモデルの中古でも、普通に10万超えてます。

こりゃ手が出んばい、ってことで、ありもののMacを改造する方向でいくことに！

Macのパフォーマンス改善のため、以下の2つを行いました。

* **メモリを8GB→16GBへ増設（本記事）**
* **HDDをSSDへ換装**

結論として、**総額1.7万円弱で、個人の開発レベルでは問題ないマシン**に改造できたので、この方法を選んで正解でした。

> **※注意※**
>
> サポートとか外れるらしいのでやるなら自己責任で。



## Macのスペック

![image](2.jpg)



## 購入したものリスト

（非アフィ）

[シリコンパワー ノートPC用メモリ DDR3 1600 PC3-12800 8GB×2枚 204Pin Mac 対応 永久保証 SP016GBSTU160N22](https://www.amazon.co.jp/gp/product/B0094P98FK/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1)

![image](3.jpg)



[アネックス(ANEX) 精密ドライバー +00×50 No.3450](https://www.amazon.co.jp/gp/product/B002SQLEIG/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1)

![image](4.jpg)



# 8GBのメモリを抜き取る

電源を落とし、裏返してねじをとります。長いのと短いのがあるので、場所を覚えておきましょう。静電気にはご注意。

![image](5.jpg)

蓋を開けます。奥から手前に持ち上げる感じで。

![image](6.jpg)

メモリはこいつですね。

![image](7.jpg)

意外とホコリがたまってます。せっかくの機会なので、お手持ちのダスターで掃除しておきましょう。

![image](8.jpg)

爪を左右に開くと、メモリが斜めにせりあがるので、ひっぱって抜きます。2枚あるのでどちらも。

![image](9.jpg)

![image](10.jpg)



# 16GBのメモリをさす

メモリを抜くときと逆の手順で刺します。斜めにさして、水平になるよう押し込みます。

特に難しいことはないので画像はなし。



# Mac起動

起動して、リンゴマーク->「このMacについて」で確認しましょう！

しっかり認識されてメモリが16GBに変わっています！

![image](11.jpg)

メモリ増設により、アプリ起動速度がほんの少し上がります。

しかし、やはり実用に耐えうる速度ではありません。

続けてSSD換装です！次回に続く。

→ [MacBook Pro Mid 2012をSSD換装](https://blog.kouki.io/2019/10/macbook-ssd/)



# 参考

[MacBook Pro (13-inch, Mid 2012)のメモリ増設して16GBにした](https://t32k.me/mol/log/macbook-pro-how-to-remove-and-install-memory/)

[超快適！MacBook Pro Mid2012のメモリの増設方法](https://like-apple.com/macbook-pro-memory/)

