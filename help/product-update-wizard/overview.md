---
title: 製品アップデートウィザード
description: 製品アップデートウィザードを使用して、Cloud Manager 内でのエンドツーエンドの AEM アップデートプロセスを合理化する方法について説明します。
exl-id: 8134e956-bfcf-41b8-a408-fa4375058c6a
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 82%

---


# 製品アップデートウィザード {#product-update-wizard}

製品アップデートウィザードでは、Cloud Manager を使用して、最新バージョンの Adobe Experience Manager 6.5 へとガイドに従って段階的にアップグレードできます。エンドツーエンドのプロセスを合理化し、Cloud Managerの CI/CD フレームワークと組み込みの自動テストを使用して、AEMのベストプラクティスに準拠していることを確認します。

このウィザードには、AEM 製品のアップデート時にユーザーをガイドする次の 5 つの段階が含まれています。

* 評価
* 修正
* 実行
* 検証
* 完了

## ウィザードの使用 {#using}

Cloud Manager にオンボーディングしており、AEM 6.5 へのアップグレード対象となっている顧客は、製品アップデートウィザードを利用できます。詳しくは、カスタマーサクセスエンジニア（CSE）にお問い合わせください。

1. AEM 6.5 がプログラムで使用可能なことを知らせるプッシュ通知が Cloud Manager を通じて送られます。

1. **[!UICONTROL AEM 6.5 アップデート]**&#x200B;カードが [!UICONTROL Cloud Manager] の概要画面に表示されます。このカードは、アップデートプロセスの現在の段階を追跡するのに役立ち、次に実行するステップについて知らせます。

   ![アップデートウィザードカード](/help/assets/Start-Update.png)

1. 「**[!UICONTROL アップデートを開始]**」を選択して、ウィザードを起動します。

1. ウィザードには、**[!UICONTROL AEM 6.5 アップデート]**&#x200B;プロセスの第 1 段階が表示されます。

ウィザードの第 1 段階について詳しくは、ドキュメント [ 評価段階 ](/help/product-update-wizard/evaluation.md) を参照してください。

