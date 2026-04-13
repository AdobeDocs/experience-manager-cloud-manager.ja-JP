---
title: 開発環境のサービスパックの更新 – プライベートベータ版
description: Cloud Manager ユーザーインターフェイスを使用して、開発環境のサービスパックの更新を開始できるようになりました。
hide: true
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: 17edfbaea9bb2bd9b817a0ee5726b0883cdd31f2
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 2%

---

# 開発環境向けサービスパックの更新（プライベートベータ版） {#stage-prod-only}

Cloud Manager ユーザーインターフェイスを使用して、開発環境のサービスパックの更新を開始する方法について説明します。

>[!NOTE]
>
>この機能は、[&#x200B; プライベートベータプログラム &#x200B;](/help/release-notes/current.md#beta-program)でのみ利用できます。

## 概要 {#service-pack-updates-overview}

開発環境のサービスパックの更新は、Cloud Manager ユーザーインターフェイスを使用して開始できます。 この機能を使用すると、使用可能なサービスパックの更新を確認し、インストールプロセスを個別に管理できます。

**主なメリット**

* Cloud Manager サービスパックの更新をより詳細に制御できます。
* 更新を開始するためのAdobe カスタマーサクセスエンジニア（CSE）への依存を減らします。
* Cloud Managerを使用して、更新プロセス全体を追跡します。

**現在の制限**

* セルフサービス更新オプションは、開発環境でのみ使用できます。
* 失敗した更新に対するエラーレポートは限定的です。
* 問題が発生した場合は、Adobe CSEに連絡して詳細な調査を行う必要があります。

## サービスパックの更新を開始

1. Deployment Manager権限でCloud Managerにログインします。
1. プログラム概要ページに移動します。
1. 「環境」セクションで、![詳細アイコン、省略記号](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)をクリックします。

   ![&#x200B; ドロップダウンメニューでサービスパックの更新を確認](/help/using/assets/service-pack-check-for-updates.png)

1. ドロップダウンメニューから、![&#x200B; ライトアイコンで開く](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **アップデートを確認**&#x200B;をクリックして、使用可能なサービスパックのアップデートをスキャンします。

   ![使用可能な更新プログラムのリストが表示されます](/help/using/assets/service-pack-versions.png)

1. リストから目的のサービスパックバージョンをクリックします。
1. 「**サービスパックを更新**」をクリックして、更新プロセスを開始します。
1. 確認ダイアログボックスで、詳細を確認し、更新を確認します。

   確認が完了すると、インストールプロセスが開始され、Cloud Managerで進行状況を追跡できます。

## サービスパックの更新を追跡

更新を開始したら、Cloud Managerのアクティビティページで進行状況を監視できます。

**サービスパックの更新を追跡するには：**

1. Cloud Manager ダッシュボードからアクティビティページに移動します。
1. サービスパックインストール エントリを探します。

   ![&#x200B; サービスパックのインストール &#x200B;](/help/using/assets/service-pack-installation.png)

1. エントリをクリックすると、次のような詳細な進行状況とステータスの更新が表示されます。

   ![&#x200B; サービスパックのインストールの進行状況](/help/using/assets/service-pack-progression.png)

### インストールエラーのトラブルシューティング

* インストールに失敗した場合は、Cloud Managerによってロールバックが以前のステートに自動的にトリガーされます。
* 問題が解決しない場合は、「**ログをダウンロード**」をクリックしてエラーログを収集し、Adobe サポートに問い合わせてトラブルシューティングを行います。

## サービスパックの実行を承認または却下

インストールが完了したら、更新を確定するために承認（または拒否）が必要です。

**サービスパックの実行を承認または却下するには：**

1. Cloud Managerでアクティビティページを開きます。
1. サービスパックの更新に対する保留中の承認リクエストを探します。

   ![&#x200B; サービスパックの更新を却下または承認](/help/using/assets/service-pack-reject-approve.png)

1. 次のいずれかの操作を行います。

   * 更新を確定するには、**承認**&#x200B;をクリックします。

   ![&#x200B; サービスパックの承認](/help/using/assets/service-pack-approve.png)

   * 更新をキャンセルするには、**拒否**&#x200B;をクリックします。
サービスパックのインストールがキャンセルされ、変更は適用されません。

   ![&#x200B; サービスパックの拒否](/help/using/assets/service-pack-reject.png)
