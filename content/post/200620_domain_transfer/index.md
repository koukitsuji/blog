---
title: "AWS Route53からGoogle Domainsへドメインを移管"
date: 2020-06-20T12:07:09+09:00
slug: domain-transfer
draft: false

# post thumb
image: "logo.jpg"

# meta description
description: "AWS Route53で購入したドメインを、Google Domainsへ移管する方法です。"

# taxonomies
categories:
  - "Programming"
tags:
  - "blog"
  - "GCP"
  - "AWS"

# post type
type: "post"
---



# はじめに

Amazon Web Service (AWS) のドメインネームシステム (DNS) である [Amazon Route 53](https://aws.amazon.com/jp/route53/) から、Google Cloud Platform (GCP) の [Google Domains](https://domains.google/intl/ja_jp/) へ、ドメインを移管します。

[以前の記事](https://blog.kouki.io/2020/06/hugo-blog/)で言及したように、Hugo + Firebase Hosting でブログを構成するので、カスタムドメインもGoogle系サービスで管理することが目的です。

基本的に、公式ドキュメント通りにやればいけます。



## 前提

* AWS Route 53でドメインを取得済み
* AWSで配信していたコンテンツのGCPへの移行は考慮しない（ドメインの移管のみ行う）



## Prerequisite

* AWSアカウント
* AWS Route53で取得したドメイン
* GCPアカウント
* macOS Mojave 10.14.6



## 本記事でやること

* AWS Route53で購入したドメインを、Google Domainsへ移管





# AWSでの作業

AWS公式  [Amazon Route 53 から別のレジストラへのドメインの移管](https://docs.aws.amazon.com/ja_jp/Route53/latest/DeveloperGuide/domain-transfer-from-route-53.html) を参考にします。



## Cloud Front のディストリビューションの削除

移管するドメイン / サブドメインがCloud Frontで使用されている場合は、コンテンツとの関連付けを削除します。

[Cloud Front](https://console.aws.amazon.com/cloudfront/home) からコンソールへログインし、移管するドメインを無効化し、削除します。



## Certicification Managerで証明書の削除



[Certification Manager](https://console.aws.amazon.com/acm/home) から、移管したいドメイン / サブドメインの証明書を削除します。

（Cloud Frontで使用したままだと、ステータスが「使用中」となり削除できないので注意）



## Route 53で操作



1. [Route 53](https://console.aws.amazon.com/route53/) へアクセス
2. ナビゲーションの「登録済みドメイン」を開く
3. 「ドメイン名」から、移管したいドメインを開く
4. 「移管のロック」を無効化
5. 「認証コード」をメモ



ここで、「ドメイン名のステータスコード」が「OK」ではなく、エラーメッセージが表示されているときは移管できません。私の場合は以下の2つが表示されており、それぞれ別の手段で解決しました。



* **clientTransferProhibited**: 「移管のロック」を無効化することで解決しました
* **serverTransferProhibited**: AWSサポートへ問い合わせて解決してもらう必要があります。[ここ](https://docs.aws.amazon.com/ja_jp/Route53/latest/DeveloperGuide/domain-contact-support.html)を参考に問い合わせましょう

私の場合も、**serverTransferProhibited**のステータスだったため問い合わせたところ、AWSサポートから以下の返答が来ました。

>.ioを含め多くのドメインではドメイン登録後 60 日経過するまでは
>別のレジストラへ移管できないよう "serverTransferProhibited"のステータスが付与される仕様となっております。
>
>今回のドメインの場合には、ご登録から 60 日間が経過しておりますので、
>通常であればこのステータスではコンソール上でも更新されるべきですが、
>60日経過後ドメイン移管が可能な状態になっても、コンソール上のステータス表記だけ更新されない場合がございます。
>
>このたびは担当部署にて確認しましたところ、今回のケースもコンソール上のステータス表記のみが古い状態であり、
>ドメイン自体は移管可能な状態になっているとの事でございました。
>（.io の who is 検索で該当ドメインを検索した場合も Domain Status が"serverTransferProhibited"のステータスではない事を確認いただけます。）





# Google Domainsでの操作



AWS側での準備が終了したら、[Google Domains](https://domains.google/intl/ja_jp/)へアクセスし、``[移管]``より、必要事項を記入して購入します。



![1](1.jpg)





先程AWSでメモした認証コードが必要です。



![2](2.jpg)





数分すると、移管が完了し利用可能となります。



以上です。