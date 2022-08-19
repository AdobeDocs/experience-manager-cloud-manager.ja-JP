---
title: 環境のプロビジョニング
description: Cloud Manager のオンボーディングプロセスの一環として環境をプロビジョニングする方法について説明します。
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: d033b7cf53d4d9faf074f1dc09e2958eb91afe3b
workflow-type: ht
source-wordcount: '314'
ht-degree: 100%

---


# 環境のプロビジョニング {#environments-provisioning}

Cloud Manager のオンボーディングプロセスの一環として環境をプロビジョニングする方法について説明します。

## プロビジョニング {#provisioning}

オンボーディングプロセス中に、購入したすべての AEM クラウド環境がアドビによって自動的にプロビジョニングされ、[!UICONTROL Cloud Manager] 内のプログラムにリンクされます。これらの AEM クラウド環境は、どの Adobe Managed Services サブスクリプションにも含まれ、通常は 1 つ以上の実稼働環境、1 つのステージング環境、1 つ以上の開発環境またはテスト環境（オプション）で構成されます。

## お知らせメール {#welcome-email}

環境プロビジョニングプロセスが完了すると、Adobe [!UICONTROL Experience Cloud] へのアクセス権を付与されたことを確認するお知らせメールが顧客側の指定管理者に届きます。このお知らせメールには、[!UICONTROL Experience Cloud] サービス、[!UICONTROL AEM Managed Services] クラウド環境および [!UICONTROL Cloud Manager] セルフサービスポータルの使用を開始する方法が詳しく記載されています。さらに、このメールには、カスタマーサクセスエンジニア（CSE）の連絡先情報のほか、サポートリソース、フォーラム、FAQ などの URL といった重要な情報も含まれています。このメールに記載されているリソースの一覧には、AEM クラウド環境の [!UICONTROL Cloud Manager] にアクセスする方法の詳細も記載されています。

## 次の手順 {#next-steps}

お知らせメールが届くと、Adobe IMS 資格情報を使用してシステム管理者として [!UICONTROL Cloud Manager] にログインする準備が整います。ログインすれば、AEM クラウドの実稼動環境および非実稼動環境が使用可能で正常に動作していることを確認できます。

これらの AEM クラウド環境は、[!UICONTROL Cloud Manager] の Git リポジトリからステージング環境を通じて AEM 実稼動環境までコードをデプロイする際に、[!UICONTROL Cloud Manager] で CI／CD パイプラインを実行するために使用されます。また、web プロパティのデジタルエクスペリエンスの作成を開始する準備ができたら、[!UICONTROL Cloud Manager] から直接 AEM クラウド環境にアクセスすることもできます。
