---
title: "MacBook Pro Mid 2012をSSD換装"
date: 2019-10-04T23:04:18+09:00
update: 2020-04-11T23:04:18+09:00
slug: macbook-ssd
draft: false

# post thumb
image: "1.jpg"

# meta description
description: "HDを自力でSSD換装し、総額1.7万円でMacBook Pro Mid 2012を使用可能なマシンへ復活させた方法です。"

# taxonomies
categories:
  - "Programming"
tags:
  - "MacBook"

# post type
type: "post"
---

# はじめに

Macふっかつ計画パート２です。

前回のメモリ増設はこちら。

→ [MacBook Pro Mid 2012のメモリを16GBへ増設](https://blog.kouki.io/2019/10/macbook-memory/)

``MacBook Pro Mid 2012 (13インチ)``のストレージはHDDですので、SSD換装が最もパフォーマンスへのインパクトの大きい改善になります。

> **※注意※**
>
> やるなら自己責任で。


## Macのスペック


[前回](//FIXME)、メモリを16GBへ増設済みですので、標準とはスペックが異なります。

![image](2.jpg)

## 購入したものリスト

（非アフィ）

[Samsung SSD 500GB 860EVO 2.5インチ内蔵型【PlayStation4 動作確認済】5年保証 正規代理店保証品 MZ-76E500B/EC](https://www.amazon.co.jp/gp/product/B07969N2W9/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1)

![image](3.jpg)

[アネックス(ANEX) 精密ドライバー +00×50 No.3450](https://www.amazon.co.jp/gp/product/B002SQLEIG/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1)

![image](4.jpg)

[アネックス(ANEX) T型ヘクスローブドライバー T6×50 No.6300](https://www.amazon.co.jp/gp/product/B002SQLDSM/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1)

![image](5.jpg)


# バックアップをとる

必ずバックアップを取りましょう。

私はMacを全く使っていなかったため、ミュージックを外付けHDDへ退避させる程度でした。
ちゃんとやるならTime Machineなど、お好みのツールをお使いください。

# HDDを抜き取る

[前回](//FIXME)と同様の手順で、電源を落とした後、Macの裏蓋を取ります。静電気には気を付けましょう。

ねじを取り、

![image](6.jpg)

蓋をあけます。

![image](7.jpg)

HDDは左下のこいつですね。

![image](8.jpg)

HDD上部の固定具のねじを緩めます（全部は取れません）。

![image](9.jpg)

無くさないようにしましょう。

![image](10.jpg)

HDDを慎重に抜きます。コネクタはHDDの左側にあります。

![image](11.jpg)

HDDについているネジを4つ抜きます。これはSSDをMacへ固定するために必要なパーツです。

![image](12.jpg)


# SSDをMacへ差す

HDDを抜き取ったのと、逆の手順で差していきます。

これも特に難しくないので写真は割愛します。


# SSDをフォーマットし、Mac OSをインストール

電源を入れてすぐ「command⌘ + R」を押し続けて、リカバリーモードへ入ります。

以下のように、地球儀が出てくるとリカバリーモードへ正しく入れていますので少し待ちます。

![image](13.jpg)

「OS X ユーティリティ」→「ディスクユーティリティ」を選択します。

![image](14.jpg)

「ディスク」→「消去」→「Mac OS 拡張（ジャーナリング）」→「名称設定」→「消去」でSSDをフォーマットします。

![image](15.jpg)

フォーマットが完了したら、Mac OSをインストールします。

Mac X Mountain Lionがインストールされます。

![image](16.jpg)

インストールが完了したら、適当に設定してログインします。ストレージがSSDになってますね！やりました！

![image](17.jpg)

次に、OSをMojaveへアップグレードします。

![image](18.jpg)

![image](19.jpg)


# macOS Mojaveをクリーンインストール

せっかくですので、クリーンインストールをやります！

電源を入れなおして、「command⌘ + R」により再び「macOS ユーティリティ」へ入ります。

macOS Mojaveを入れた後ですので、ここも先ほどと変わってますね。

![image](20.jpg)

同様に、ディスクユーティリティからSSDをAPFSで再フォーマットします。

![image](21.jpg)

OSを入れると、今度はいきなりmacOS Mojaveがインストールされます。

![image](22.jpg)

![image](23.jpg)

グッド。

![image](2.jpg)


# TRIMを有効化

SSDの劣化を遅らせるため、ターミナルから以下のコマンドを叩きTRIMを有効化します。

```bash
$ sudo trimforce enable
```

詳細は参考のWEBページを参照。


# おわりに

これで、MacのSSD換装は完了です！

もう全く違うマシンですね。これなら個人レベルでの開発程度なら、あと数年は使えるんじゃないでしょうか。

お疲れさまでした＼(^o^)／


# 参考

[MacBook Pro 2012midモデルをSSDに換装したらめちゃくちゃ快適なMacになりました](https://www.useful-time.com/entry/ssd)

[macOS Mojave をクリーンインストールする手順！](https://ischool.co.jp/2018-09-26/)

[MacでSSDの速度を向上させる(速度低下を防ぐ)「TRIM機能」を有効化する](https://sekinesan.jp/blog/2017/05/17/17061)
