---
title: 環境のプロビジョニング
description: Cloud Manager のオンボーディングプロセスの一環として環境をプロビジョニングする方法について説明します。
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 36%

---


# 環境のプロビジョニング {#environments-provisioning}

Cloud Manager のオンボーディングプロセスの一環として環境をプロビジョニングする方法について説明します。

## プロビジョニング {#provisioning}

オンボーディングプロセス中に、Adobeは購入したすべてのAEM クラウド環境を自動的にプロビジョニングし、[!UICONTROL Cloud Manager] のプログラムにリンクします。 すべてのAdobe Managed Services サブスクリプションには、AEM クラウド環境が含まれます。 通常、これには少なくとも 1 つの実稼動環境と 1 つのステージング環境が含まれます。 オプションで、1 つ以上の開発環境またはテスト環境を含めることもできます。

## お知らせメール {#welcome-email}

環境プロビジョニング・プロセスが完了すると、Adobe[!UICONTROL Experience Cloud] へのアクセス権が付与されたことを確認するお知らせメールが顧客側の指定管理者に届きます。 ウェルカムメールには、[!UICONTROL Experience Cloud] サービス、[!UICONTROL AEM Managed Services] クラウド環境および [!UICONTROL Cloud Manager] セルフサービスポータルの使用を開始する方法が詳しく記載されています。さらに、このメールには、カスタマーサクセスエンジニア（CSE）の連絡先情報のほか、サポートリソース、フォーラム、FAQ などの URL といった重要な情報も含まれています。このメールに記載されているリソースの一覧には、AEM クラウド環境の [!UICONTROL Cloud Manager] にアクセスする方法の詳細も記載されています。

## 次の手順 {#next-steps}

ウェルカムメールが届くと、Adobe IMS 資格情報を使用してシステム管理者として [!UICONTROL Cloud Manager] にログインする準備が整います。ログインしたら、AEM クラウドの実稼動環境および非実稼動環境が使用可能で、スムーズに動作していることを確認できます。

[!UICONTROL Cloud Manager] は、これらのAEM クラウド環境を使用して CI/CD パイプラインを実行します。 Git リポジトリからステージング環境にコードをデプロイします。 その後、コードをAEM実稼動環境にデプロイします。 Web プロパティのデジタルエクスペリエンスの作成を開始する準備ができたら ][!UICONTROL Cloud Managerから直接AEM クラウド環境にアクセスすることもできます。
