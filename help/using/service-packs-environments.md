---
title: 開発環境のサービスパックの更新 – 早期導入
description: Cloud Manager ユーザーインターフェイスを使用して、開発環境のサービスパックのアップデートを開始する方法について説明します。
hide: true
hidefromtoc: true
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: 55b33db1bf80f066b1a66bc87c0abeefa4771871
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---

# 開発環境のサービスパックの更新（早期導入） {#stage-prod-only}

Cloud Manager ユーザーインターフェイスを使用して開発環境のサービスパックのアップデートを開始する方法について説明します。

>[!NOTE]
>
>この機能は、[早期導入プログラム](/help/release-notes/current.md#early-adoption)でのみ利用できます。

## 概要 {#service-pack-updates-overview}

Cloud Manager ユーザーインターフェイスを使用して、開発環境のサービスパックのアップデートを開始できます。 この機能を使用すると、利用可能なサービスパックのアップデートを確認し、インストールプロセスを個別に管理できます。

**主なメリット**

* Cloud Manager サービスパックのアップデートをより詳細に制御できます。
* アップデートを開始する際に、Adobe カスタマーサクセスエンジニア（CSE）への依存度を軽減します。
* Cloud Managerを使用して更新プロセス全体をトラッキングします。

**現在の制限事項**

* セルフサービス更新オプションは、開発環境でのみ使用できます。
* 失敗した更新に関する限定的なエラーレポートを利用できます。
* 問題が発生した場合は、Adobe CSE に問い合わせて詳細を確認する必要があります。

## サービスパックの更新を開始

1. デプロイメントマネージャー権限でCloud Managerにログインします。
1. プログラムの概要ページに移動します。
1. 「環境」セクションで、![ 詳細アイコン、省略記号 ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) をクリックします。

   ![ ドロップダウンメニューでサービスパックの更新を確認 ](/help/using/assets/service-pack-check-for-updates.png)

1. ドロップダウンメニューから ![Open in light icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg)**Check for Updates** をクリックし、利用可能なサービスパックの更新をスキャンします。

   ![ 利用可能なアップデートのリストが表示されます ](/help/using/assets/service-pack-versions.png)

1. リストから目的のサービスパックバージョンをクリックします。
1. **サービスパックを更新** をクリックして、更新プロセスを開始します。
1. 確認ダイアログボックスで詳細を確認し、更新を確定します。

   確認すると、インストールプロセスが開始され、Cloud Managerで進行状況を追跡できます。

## サービスパックの更新を追跡

更新を開始した後、Cloud Managerのアクティビティページで進行状況を監視できます。

**サービスパックの更新を追跡するには：**

1. Cloud Manager ダッシュボードからアクティビティページに移動します。
1. サービスパックのインストールエントリを探します。

   ![ サービスパックのインストール ](/help/using/assets/service-pack-installation.png)

1. エントリをクリックすると、次のような詳細な進行状況とステータスの更新が表示されます。

   ![ サービスパックのインストールの進行状況 ](/help/using/assets/service-pack-progression.png)

### インストール失敗のトラブルシューティング

* インストールに失敗した場合は、Cloud Managerによって自動的に以前のステートへのロールバックがトリガーされます。
* 問題が解決しない場合は、「**ログをダウンロード**」をクリックしてエラーログを収集し、トラブルシューティングについてAdobe サポートにお問い合わせください。

## Service Pack の実行を承認または拒否

インストールが完了したら、更新を完了するために承認（または却下）が必要です。

**Service Pack の実行を承認または拒否するには：**

1. Cloud Managerでアクティビティページを開きます。
1. サービスパック更新の承認待ちリクエストを見つけます。

   ![Service Pack の更新を拒否または承認 ](/help/using/assets/service-pack-reject-approve.png)

1. 次のいずれかの操作を行います。

   * 更新を完了するには、「**承認**」をクリックします。

   ![ サービスパックの承認 ](/help/using/assets/service-pack-approve.png)

   * 更新をキャンセルするには、「**却下**」をクリックします。
サービスパックのインストールがキャンセルされ、変更は適用されません。

   ![ サービスパックの拒否 ](/help/using/assets/service-pack-reject.png)
