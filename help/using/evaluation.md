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
source-git-commit: 9a1af88238a232c64d9f0229059c5001f314c736

---


# Evaluation Phase {#evaluation}

Once you click **[!UICONTROL Start Update]**, the first phase in Product Update wizard is the **[!UICONTROL Evaluation]** phase. この段階では、ウィザードから直接アクセスできるパターン検出機能を使用して、アップグレードの複雑さを評価できます。この手順の最後に、評価レポートにアクセスできます。

生成されたレポートでは、次のパターンを検出して、アップグレード可能性の作成者インスタンスを確認できます。

* 特定のルールに違反し、アップグレードに影響または上書きされる領域で実行されます。

* AEM6. xの機能または新しいAEMで下位互換性のないAPIを使用して、アップグレード後に中断する可能性がある可能性があります。

これは、Adobe Experience Manager（AEM）6.5へのアップグレードに関与する開発作業の査定として機能します。

>[!NOTE]
>To learn more about pattern detector, refer to [Assessing the Upgrade Complexity with the Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Running the Evaluator {#running-evaluator}

評価基準を実行するには、次の手順に従います。

1. Click on **[!UICONTROL Run Evaluation]** to run the pattern detector.

   >[!NOTE]
   >パターン検出は任意の環境で実行できます。ただし、検出率を向上させ、ビジネス重要インスタンスの低下を防ぐために、Cloud Managerは作成者インスタンス上のステージング環境で実行します。

   ![](assets/Run-Evaluation.png)

1. ウィザードによってアクションのステータスが通知されます。You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

   Once the report is generated, you can click on **[!UICONTROL Download report]** to save a copy of the evaluation report.

   ![](assets/Evaluation-1.png)

   Additionlyでは、更新されたパルス通知をステータス更新として表示できます。

   ![](assets/Evaluation-pulse-notification.png)

>[!NOTE]
>The other four phases succeeding **Evaluation** namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon and are not available in the current release.
