---
title: "Oculus Quest実機のVR空間内でデバッグログを表示"
date: 2020-07-22T02:24:11+09:00
slug: oculus-debuglog
draft: false

# post thumb
image: "logo.jpg"

# meta description
description: "Oculus Questで実機ビルドする際、VR空間内でデバッグ用のログを表示する方法です。"

# taxonomies
categories:
  - "VR"
tags:
  - "OculusQuest"
  - "VR"
  - "Unity"

# post type
type: "post"
---



# はじめに

Unityで作成したアプリを`Oculus Quest`で実機ビルドすると、Unityの`Debug.Log();`によるデバッグログ表示ができずになにかと不便です。

そもそも、OculusアプリはUnity上で再生できず実機ビルド必須なので、VR空間内にリアルタイムなログ表示を行わないと作業効率が低下します。

ということで、以下のようなものを実装する方法です。

{{< tweet 1285582260754767872 >}}

では、行きましょう。

## 開発環境

* macOS Mojave 10.14.6
* Unity 2019.4.4f1 LTS
* OculusIntegration_v17.0.unitypackage

# まとめ

* `Assets > Oculus > SampleFramework > Usage > DebugUI`を参照
* 自分のSceneへ`CanvasWithDebug`を追加
* `DebugUISample.cs`の内容をコピーし、自身のスクリプトを作成。適当なゲームオブジェクトへアタッチ

# SampleFrameworkのDebugUIを参照

まずは、`Oculus Integration`の`Assets > Oculus > SampleFramework > Usage > DebugUI`を参照しましょう。

ここに必要な情報がすべてあります。

![0](0.jpg)

以下は、Oculus公式の解説ページです。

[DebugUIサンプルシーン](https://developer.oculus.com/documentation/unity/unity-sf-debugui/?locale=ja_JP)

# 自分のシーンへCanvasWithDebugを追加

`DebugUI`シーンを参考に、まず自分のシーンへ以下を追加します。

* CanvasWithDebug

こいつが、VR空間上にデバッグUIを表示するためのものです。

![1](1.jpg)

# DebugUISample.csを確認

さらに、`DebugUI`シーンの`SampleSupport`にアタッチされた`DebugUISample.cs`を確認します。

![2](2.jpg)

この中で呼ばれている`DebugUIBuilder`が重要で、こいつに追加することでテキストやらボタンやらスライダーやらを`CanvasWithDebug`へ追加できます。

（この詳細は`DebugUIBuilder.cs`を読めば分かります。）

`DebugUI`シーンと同じ環境を作るには、

* 自分のシーンでゲームオブジェクトを作成
* `DebugUISample.cs`の内容をそのままコピーしたスクリプトを新たに作成し、作成したゲームオブジェクトへアタッチ

![3](3.jpg)

これで、`DebugUI`シーンと同じ環境が作れます。

（上の画像では追加で、`OvrPlayerController`と、床となる適当なオブジェクトを追加し、メインカメラを削除する必要があります）

# DebugUIBuilderの呼び出し

これは、シーン内の様々なスクリプト内でどこでも呼び出すことができます。

たとえば、接触判定する際の`OnTriggerEnter`内で呼び出し、テキストを追加することで、VR内のデバッグプリントを行うことができるようになります。

そのような使い方をする場合、上で示した`DebugUIBuilder.cs`のコピペは不要となります。

`DebugUIBuilder.cs`は、コードをいじりながら、どこをどう変更すればどう変わるかを確認する程度でよいでしょう。

# おわりに

意外とOculusのデバッグログ表示の記事が少なく苦労しました。

数少ない記事も、情報が古かったり、私のようなUnity初心者からすれば何をやっているか分からないくらい省略されていたりで…

ですが、実際に自分で書いてみると、Unityの設定は意外と細かい手順が多く、いちいち丁寧に説明するのは非常にコストがかかるのですね。

一応、本記事も、どこを読めば分かるというのは明示しているので、分かるはず…です。