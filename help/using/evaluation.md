---
title: 評価
seo-title: 評価
description: 'このページは、製品アップデートウィザードの評価段階の開始点として機能します。 '
seo-description: このページは、製品アップデートウィザードの評価段階の開始点として機能します。
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER／CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: 9e33b90818c686f0b7aacaf0955c3f2eba05488f

---


# Evaluation Phase {#evaluation}

The first phase in the Product Update wizard is **[!UICONTROL Evaluation]** phase.
ここでは、ウィザードから直接アクセスできるパターン検出機能を使用して、アップグレードの複雑さを評価できます。この手順の最後に、評価レポートにアクセスできます。

生成されたレポートでは、次のパターンを検出して、アップグレード可能性の作成者インスタンスを確認できます。

* 特定のルールに違反し、アップグレードに影響または上書きされる領域で実行されます。

* AEM6. xの機能または新しいAEMで下位互換性のないAPIを使用して、アップグレード後に中断する可能性がある可能性があります。

これは、Adobe Experience Manager（AEM）6.5へのアップグレードに関与する開発作業の査定として機能します。

>[!NOTE]
>To learn more about pattern detector, refer to [Assessing the Upgrade Complexity with the Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Running the Evaluator {#running-evaluator}

評価レポートを生成するには、次の手順に従います。

1. Click on **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
   >パターン検出は任意の環境で実行できます。ただし、検出率を向上させ、ビジネス重要インスタンスの低下を防ぐために、Cloud Managerは作成者インスタンス上のステージング環境で実行します。

   ![](assets/Run-Evaluation.png)

1. ウィザードによって、アクションのステータスが通知されます。You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

   Once the report is generated, you can click on **[!UICONTROL Download report]** to save a copy.

   ![](assets/Evaluation-1.png)


>[!NOTE]
>The current release of Product Update wizard in Cloud Manager supports the **Evaluation** phase only. **「修正」**、 **「実行」**、 **「検証」** および「 **完了」** の4段階は、近日中に提供されます。
