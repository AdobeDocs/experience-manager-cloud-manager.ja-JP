---
title: 評価
seo-title: 評価
description: 'このページは、製品アップデートウィザードの評価段階を理解するための出発点となります。 '
seo-description: このページは、製品アップデートウィザードの評価段階を理解するための出発点となります。
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: 8d1a100420129d234fe21911f165621405a04a9b
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 100%

---


# 評価段階 {#evaluation}

製品アップデートウィザードの第 1 段階は&#x200B;**[!UICONTROL 評価]**段階です。
ここでは、ウィザードから直接アクセスできるパターン検出を使用して、アップグレードの複雑さを評価できます。このステップの終わりに、評価レポートにアクセスできます。

生成されたレポートでは、次のパターンを検出することで、オーサーインスタンスのアップグレードをチェックできます。

* 特定のルールに違反しており、アップグレードで影響を受けるか上書きされる領域で実行されている。

* 新しい AEM との下位互換性のない AEM 6.x 機能や API を使用しており、アップグレード後に動作しない可能性がある。

これにより、Adobe Experience Manager（AEM）6.5 へのアップグレードに必要な開発作業量を評価できます。

>[!NOTE]
>
>パターン検出について詳しくは、[パターン検出を使用したアップグレードの複雑性の評価](https://docs.adobe.com/content/help/ja-JP/experience-manager-64/deploying/upgrading/pattern-detector.translate.html)を参照してください。

## エバリュエーターの実行 {#running-evaluator}

評価レポートを生成するには、次の手順に従います。

1. 「**[!UICONTROL 評価を実行]**」をクリックします。

   >[!NOTE]
   >
   >パターン検出はどのような環境でも実行できます。ただし、検出率を向上させ、ビジネスクリティカルなインスタンスの速度低下を避けるために、Cloud Manager ではオーサーインスタンス上のステージング環境でパターン検出を実行します。

   ![](assets/Run-Evaluation.png)

1. ウィザードから、アクションのステータスが通知されます。評価レポートの生成中に、**進行中**&#x200B;または&#x200B;**完了**&#x200B;が適宜表示されます。

   レポートが生成されたら、「**[!UICONTROL レポートのダウンロード]**」をクリックしてコピーを保存できます。

   ![](assets/Evaluation-1.png)


   >[!NOTE]
   >
   >Cloud Manager における製品アップデートウィザードの現在のリリースでは、**評価**&#x200B;段階のみサポートされています。**修正**、**実行**、**検証**、**完了**&#x200B;の 4 段階は、現在準備中です。
