---
title: 環境のプロビジョニング
description: Cloud Manager のオンボーディングプロセスの一環として環境をプロビジョニングする方法について説明します。
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: d033b7cf53d4d9faf074f1dc09e2958eb91afe3b
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 1%

---


# 環境のプロビジョニング {#environments-provisioning}

Cloud Manager のオンボーディングプロセスの一環として環境をプロビジョニングする方法について説明します。

## プロビジョニング {#provisioning}

オンボーディングプロセス中、購入したすべてのAEMクラウド環境はAdobe別に自動的にプロビジョニングされ、 [!UICONTROL Cloud Manager]. これらのAEMクラウド環境は、すべての Adobe Managed Services サブスクリプションに含まれ、通常は 1 つ以上の実稼動環境、1 つのステージング環境、1 つ以上の開発環境またはテスト環境（オプション）で構成されます。

## お知らせメール {#welcome-email}

環境プロビジョニングプロセスが完了すると、Adobeへのアクセス権を付与されたことを確認するお知らせメールが顧客側の指定管理者に届きます [!UICONTROL Experience Cloud]. 「ようこそ」の電子メールには、の使用開始方法の詳細が記載されています。 [!UICONTROL Experience Cloud] サービス [!UICONTROL AEM Managed Services] クラウド環境、および [!UICONTROL Cloud Manager] セルフサービスポータル。 さらに、電子メールには、カスタマーサクセスエンジニア (CSE) の連絡先情報や、サポートリソース、フォーラム、FAQ などの重要な情報が含まれています。 電子メールに記載されているリソースのリストで、 [!UICONTROL Cloud Manager] AEMクラウド環境用に作成されます。

## 次の手順 {#next-steps}

お知らせメールが届くと、次のサイトにログインする準備が整います： [!UICONTROL Cloud Manager] システム管理者として、システムの資格情報を使用してAdobe IMSを管理します。 ログインすると、AEMクラウドの実稼動環境および非実稼動環境が使用可能で正常に動作していることを確認できます。

これらのAEMクラウド環境は、 [!UICONTROL Cloud Manager] を使用して CI/CD パイプラインを実行します。 [!UICONTROL Cloud Manager]の git リポジトリ ( ステージング環境を通じて、AEM実稼動環境まで )。 また、AEMクラウド環境には、 [!UICONTROL Cloud Manager] web プロパティのデジタルエクスペリエンスの作成を開始する準備が整ったら、次の手順に従います。
