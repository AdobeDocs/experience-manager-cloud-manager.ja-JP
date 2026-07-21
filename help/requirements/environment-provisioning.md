---
title: 環境のプロビジョニング
description: Cloud Manager のオンボーディングプロセスの一環として環境をプロビジョニングする方法について説明します。
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
TQID: https://experienceleague.adobe.com/xLjZdRZeCiqF0KxHQ1nBI4IBBsh4BDTqETv79lrypR0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 02ecd16a1735fe37ac606d275da0f61406841f56
workflow-type: tm+mt
source-wordcount: 287
ht-degree: 66%

---

# 環境のプロビジョニング {#environments-provisioning}

Cloud Manager のオンボーディングプロセスの一環として環境をプロビジョニングする方法について説明します。

## プロビジョニング {#provisioning}

オンボーディングプロセス中に、購入したすべての AEM クラウド環境がアドビによって自動的にプロビジョニングされ、[!UICONTROL Cloud Manager] 内のプログラムにリンクされます。 すべての Adobe Managed Services サブスクリプションには、AEM クラウド環境が含まれます。 通常、少なくとも 1 つの本番環境と 1 つのステージング環境が含まれます。 オプションで、1つ以上の開発環境またはテスト環境を含めることもできます。

## ウェルカムメール {#welcome-email}

環境プロビジョニングプロセスが完了すると、指定されたお客様の管理者は、Adobe [!UICONTROL Experience Cloud]へのアクセスが許可されたことを確認するウェルカムメールを受信します。 ウェルカムメールには、[!UICONTROL Experience Cloud] サービス、[!UICONTROL AEM Managed Services] クラウド環境および [!UICONTROL Cloud Manager] セルフサービスポータルの使用を開始する方法が詳しく記載されています。 さらに、カスタマーサクセスエンジニア（CSE）の連絡先情報、サポートリソース、フォーラム、よくある質問などがメールに記載されています。 このメールに記載されているリソースの一覧には、AEM クラウド環境の [!UICONTROL Cloud Manager] にアクセスする方法の詳細も記載されています。

## 次の手順 {#next-steps}

ウェルカムメールを受け取ったら、Adobe IMSの資格情報を使用して、[!UICONTROL Cloud Manager]にシステム管理者としてログインできます。 ログイン後、AEMの本番環境と非本番環境が正常に機能していることを確認できます。

[!UICONTROL Cloud Manager] は、これらの AEM クラウド環境を使用して、CI/CD パイプラインを実行します。 Git リポジトリからステージング環境にコードをデプロイします。 次に、コードを AEM 本番環境にデプロイします。 また、web プロパティのデジタルエクスペリエンスの作成を開始する準備ができたら、[!UICONTROL Cloud Manager] から直接 AEM クラウド環境にアクセスすることもできます。
