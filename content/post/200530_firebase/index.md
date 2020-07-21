---
title: "ブログをHugo+Firebase Hosting+カスタムドメインで構成"
date: 2020-05-31T00:38:23+09:00
slug: firebase
draft: true

# post thumb
image: "1.jpg"

# meta description
description: "Hugoで生成した静的コンテンツをGoogle Firebase Hositingで配信する方法です。カスタムドメインも同時に設定します。"

# taxonomies
categories:
  - "Programming"
tags:
  - "Mediapipe"
  - "iOS"

# post type
type: "post"
---



# はじめに

静的サイトジェネレーター``Hugo``で生成したウェブサイトを、Google Firebase Hostingで安全に世の中へ配信します。

Firebaseは[無料枠](https://firebase.google.com/pricing?hl=ja)が大きいため、個人ブログ程度の規模なら無料で運用できるでしょう。

個人的に、操作が全てCLI上で完結するのもGOODです。

本ブログもHugo+Firebaseで構成しています。



## この記事でやること

* Google Firebaseの設定
* Hugoで作ったWebサイトをFirebaseへデプロイ
* カスタムドメインを設定



## 開発環境

* Mac OS: Mojave 10.14.6





# Firebaseの設定

基本的に、[Firebase公式](https://firebase.google.com/docs/hosting/quickstart?hl=ja)に従えば設定できます。



1. Firebase CLIのインストール

Firebase CLIは``npm``経由で導入するので、Node.jsの導入が前提です。

以下のコマンドでFirebase CLIをインストール。

```bash
$ npm install -g firebase-tools
```



2. Googleアカウントへログイン

```bash
$ firebase login

$ firebase projects:list
```



3. プロジェクトの初期化

Hugoプロジェクトへ移動し、Firebase用に初期化します。

```bash
$ cd HugoProject
$ firebase init

? Which Firebase CLI features do you want to set up for this folder? Press Space to select features, then Enter to confirm your choices.
 ◯ Database: Deploy Firebase Realtime Database Rules
 ◯ Firestore: Deploy rules and create indexes for Firestore
 ◯ Functions: Configure and deploy Cloud Functions
❯◉ Hosting: Configure and deploy Firebase Hosting sites
 ◯ Storage: Deploy Cloud Storage security rules
 ◯ Emulators: Set up local emulators for Firebase features
```



今回はプロジェクトを新規作成します。

```ba
? Please select an option:
  Use an existing project
❯ Create a new project
  Add Firebase to an existing Google Cloud Platform project
  Don't set up a default project
```



適当な名前を指定。今回は「testportfolio」にしました。

```bash
? Please specify a unique project id (warning: cannot be modified afterward) [6-30 characters]:
 () testportfolio
```



Hugoは配信用のコンテンツは``public``フォルダへ出力されます。したがって、FirebaseのPublishフォルダはデフォルトのpublicを指定します。

```bash
? What do you want to use as your public directory? (public)
```



index.htlmファイルの上書きはNoで

```bash
? Configure as a single-page app (rewrite all urls to /index.html)? (y/N) N
```





# Firebaseへデプロイ



以下のコマンドでHugoプロジェクトをビルドします。結果は``public``フォルダへ出力されます。

```bash
$ hugo

                   | EN
-------------------+-----
  Pages            | 36
  Paginator pages  |  0
  Non-page files   |  1
  Static files     |  5
  Processed images | 10
  Aliases          |  5
  Sitemaps         |  1
  Cleaned          |  0

Total in 470 ms
```



これをFirebaseへデプロイしましょう。

```bash
$ firebase deploy
```



実行結果として``Hosting URL``がプリントされるので、ブラウザでこのリンクへアクセスします。無事に表示されると、Firebase Hostingで自身のWebサイトが公開されていることを確認できます。

![1](1.jpg)



非常に簡単にWebページが公開出来ました。



# カスタムドメインの適用



Firebase Hostingで配信するコンテンツに、独自ドメインを適用します。



Google Domainsで購入したドメインを使用します。

まず、Hostingへアクセスし、「カスタムドメインを追加」を行います。



![2](2.jpg)



ドメインを入力します。私のポートフォリオ用のドメイン「kouki.io」を指定しています。

![3](3.jpg)



「次へ」を押すと、レコードタイプなどが表示されます。ここでの値は、Google Domainsで用います。



![4](4.jpg)





「カスタムリソースレコード」へ、先程の値を入力し「追加」します。



![5](5.jpg)



また、今回は「www.kouki.io」を「kouki.io」へリダイレクトしたいので、以下のように同じ手順を行います。



「カスタムドメインを追加」し、

![6](6.jpg)



得られた値を、



![7](7.jpg)



Google Domainsの「カスタムリソースレコード」へ追加します。



![8](8.jpg)



設定完了後しばらく待って、設定したドメインへアクセスしましょう。

正常にWebサイトが表示されれば完了です。



