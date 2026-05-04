---
title: 評価段階
seo-title: Evaluation Phase
description: 製品アップデートウィザードの評価フェーズで、パターン検出を使用してアップグレードの複雑さを評価する方法について説明します。
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
TQID: https://experienceleague.adobe.com/dj-Wnq9FagNI3mzzVHcUH-sOufzb02D0juHqhtgpon0
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 59%

---

# 評価段階 {#evaluation}

製品アップデート ウィザードの最初のフェーズは&#x200B;**[!UICONTROL 評価]** フェーズです。 ウィザード内でパターン検出を実行して、アップグレードの複雑さを評価します。 この手順の最後で、評価レポートを表示できます。

このレポートでは、次のパターンを検出することで、オーサーインスタンスのアップグレード準備状況を確認します。

* アップグレードの影響を受ける領域または上書きされた領域のルール違反。
* 下位互換性がなく、アップグレード後に壊れる可能性があるAEM 6.x機能またはAPIを使用します。

このレポートは、Adobe Experience Manager（AEM） 6.5へのアップグレードに必要な開発作業を見積もるのに役立ちます。

>[!NOTE]
>
>パターン検出について詳しくは、[パターン検出を使用したアップグレードの複雑性の評価](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector)を参照してください。

## 評価レポートの実行 {#running}

パターン検出はどのような環境でも実行できます。 ただし、検出率を高め、ビジネスクリティカルなインスタンスの速度低下を回避するには、Cloud Manager はオーサーインスタンスのステージング環境でパターン検出を実行します。

**評価レポートを実行するには：**

1. [製品アップデートウィザード](/help/product-update-wizard/overview.md)ドキュメントの説明に従って、ウィザードを起動します。

1. 「**[!UICONTROL 評価を実行]**」をクリックします。

   ![評価を実行](/help/assets/Run-Evaluation.png)

1. ウィザードから、アクションのステータスが通知されます。 評価レポートの生成中に、**進行中**&#x200B;または&#x200B;**完了**&#x200B;が適宜表示されます。

1. レポートが生成されたら、「**[!UICONTROL レポートをダウンロード]**」をクリックしてコピーを保存できます。

   ![作成されたレポート](/help/assets/Evaluation-1.png)

Cloud Managerの現在の製品アップデート ウィザードでは、**評価** フェーズのみがサポートされています。 **修正**、**実行**、**検証**、**完了**&#x200B;の 4 段階は、現在準備中です。
