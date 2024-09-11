---
title: 環境のプロビジョニング
description: Cloud Manager のオンボーディングプロセスの一環として環境をプロビジョニングする方法について説明します。
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---


# 環境のプロビジョニング {#environments-provisioning}

Cloud Manager のオンボーディングプロセスの一環として環境をプロビジョニングする方法について説明します。

## プロビジョニング {#provisioning}

オンボーディングプロセス中に、購入したすべての AEM クラウド環境がアドビによって自動的にプロビジョニングされ、[!UICONTROL Cloud Manager] 内のプログラムにリンクされます。すべての Adobe Managed Services サブスクリプションには、AEM クラウド環境が含まれます。通常、少なくとも 1 つの実稼動環境と 1 つのステージング環境が含まれます。オプションで、1 つ以上の開発環境またはテスト環境を含めることもできます。

## ウェルカムメール {#welcome-email}

環境プロビジョニングプロセスが完了すると、Adobe [!UICONTROL Experience Cloud] へのアクセス権を付与されたことを確認するウェルカムメールが顧客側の指定管理者に届きます。ウェルカムメールには、[!UICONTROL Experience Cloud] サービス、[!UICONTROL AEM Managed Services] クラウド環境および [!UICONTROL Cloud Manager] セルフサービスポータルの使用を開始する方法が詳しく記載されています。さらに、このメールには、カスタマーサクセスエンジニア（CSE）の連絡先情報のほか、サポートリソース、フォーラム、FAQ などの URL といった重要な情報も含まれています。このメールに記載されているリソースの一覧には、AEM クラウド環境の [!UICONTROL Cloud Manager] にアクセスする方法の詳細も記載されています。

## 次の手順 {#next-steps}

ウェルカムメールが届くと、Adobe IMS 資格情報を使用してシステム管理者として [!UICONTROL Cloud Manager] にログインする準備が整います。ログインすれば、AEM クラウドの実稼動環境および実稼動以外の環境が使用可能でスムーズに動作していることを確認できます。

[!UICONTROL Cloud Manager] は、これらの AEM クラウド環境を使用して、CI/CD パイプラインを実行します。Git リポジトリからステージング環境にコードをデプロイします。次に、コードを AEM 実稼動環境にデプロイします。また、web プロパティのデジタルエクスペリエンスの作成を開始する準備ができたら、[!UICONTROL Cloud Manager] から直接 AEM クラウド環境にアクセスすることもできます。
