---
title: 製品アップデートウィザード
description: 製品アップデートウィザードを使用して、Cloud Manager 内でのエンドツーエンドの AEM アップデートプロセスを合理化する方法について説明します。
exl-id: 8134e956-bfcf-41b8-a408-fa4375058c6a
TQID: https://experienceleague.adobe.com/1xLX5-Q3m0NRcAs0OrGyNbR0d2vP4VDl9iF2IzYpt7Y
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 7c68326b67ce5fc11a8afa7bffb893b461709b51
workflow-type: tm+mt
source-wordcount: 202
ht-degree: 65%

---

# 製品アップデートウィザード {#product-update-wizard}

Product Update ウィザードは、Cloud Managerを使用してAdobe Experience Manager 6.5の最新バージョンへのガイド付きシーケンシャルアップグレードエクスペリエンスです。 エンドツーエンドのプロセスを合理化し、Cloud Manager の CI/CD フレームワークとビルトインの自動テストを使用して、AEM のベストプラクティスに準拠していることを確認します。

このウィザードには、AEM 製品のアップデート時にユーザーをガイドする次の 5 つの段階が含まれています。

* 評価
* 修正
* 実行
* 検証
* 完了

## ウィザードの使用 {#using}

Cloud Manager にオンボーディングしており、AEM 6.5 へのアップグレード対象となっている顧客は、製品アップデートウィザードを利用できます。 詳細については、カスタマーサクセス担当者にお問い合わせください。

1. お客様のプログラムでAEM 6.5が利用可能であることを知らせるプッシュ通知がCloud Managerから送信されます。

1. **[!UICONTROL AEM 6.5 アップデート]**&#x200B;カードが [!UICONTROL Cloud Manager] の概要画面に表示されます。 このカードは、更新プロセスの現在のフェーズを追跡し、次に必要なステップを通知します。

   ![アップデートウィザードカード](/help/assets/Start-Update.png)

1. 「**[!UICONTROL アップデートを開始]**」を選択して、ウィザードを起動します。

1. ウィザードには、**[!UICONTROL AEM 6.5 アップデート]**&#x200B;プロセスの第 1 段階が表示されます。

ウィザードの第 1 段階について詳しくは、[評価段階](/help/product-update-wizard/evaluation.md)を参照してください。

