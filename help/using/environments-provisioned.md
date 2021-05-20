---
title: プロビジョニング済み環境
seo-title: AEM Cloud Manager のプロビジョニング済み環境
description: このページでは、Cloud Manager で使用可能なプロビジョニング済み環境について説明します。
seo-description: このページでは、AEM Cloud Manager で使用可能なプロビジョニング済み環境について説明します。
uuid: d04ee39c-7112-4adc-ad4e-56f91cc4ecfa
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: 7d32ba78-4ded-4656-aac2-c3e7cc0518de
feature: 環境、プロビジョニング
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 99%

---

# プロビジョニング済み環境 {#environments-provisioned}

## プロビジョニング {#provisioning}

顧客のオンボーディングプロセス中は、顧客が購入したすべての AEM クラウド環境がアドビによって自動的にプロビジョニングされ、[!UICONTROL Cloud Manager] のプログラムにリンクされます。これらの AEM クラウド&#x200B;**環境**&#x200B;は、すべての Adobe Managed Services サブスクリプションに含まれ、通常は 1 つ以上の実稼動環境、1 つのステージング環境、1 つ以上の開発環境またはテスト環境（オプション）で構成されます。

## お知らせメール {#welcome-email}

環境プロビジョニングプロセスが完了すると、Adobe [!UICONTROL Experience Cloud] へのアクセス権を付与されたことを確認する&#x200B;**お知らせメール**&#x200B;が顧客側の指定管理者に届きます。この電子メールには、[!UICONTROL Experience Cloud] サービス、[!UICONTROL AEM Managed Services] クラウド環境および [!UICONTROL Cloud Manager] セルフサービスポータルの使用を開始する方法が詳しく記載されています。さらに、電子メールには、カスタマーサクセスエンジニアの連絡先情報のほか、サポートリソース、フォーラム、FAQ の URL などの重要な情報も含まれています。電子メールに記載されているリソースの一覧で、[!UICONTROL Cloud Manager] またはお使いの AEM クラウド環境にアクセスする方法の詳細もわかります。

## 次の手順 {#next-steps}

お知らせメールが届くと、Adobe IMS 資格情報を使用して管理者として [!UICONTROL Cloud Manager] にログインする準備が整います。ログインすれば、AEM クラウドの実稼動環境および非実稼動環境が使用可能で正常に動作していることを確認できます。

これらの AEM クラウド環境は、[!UICONTROL Cloud Manager] の Git リポジトリからステージング&#x200B;**環境**&#x200B;を通じて AEM 実稼動環境までコードをデプロイする際に、[!UICONTROL Cloud Manager] で CI／CD パイプラインを実行するために使用されます。また、Web プロパティのデジタルエクスペリエンスの作成を開始する準備ができたら、[!UICONTROL Cloud Manager] から直接 AEM クラウド環境にアクセスできます。
