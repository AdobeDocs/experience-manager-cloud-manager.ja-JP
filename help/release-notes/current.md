---
title: リリースノート（2023.9.0）
description: Cloud Manager リリース 2023.9.0 のリリースノートです。
feature: Release Information
source-git-commit: a3e926fa13d54da1322f3a5219519fae07ddb273
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 52%

---


# Cloud Manager リリース 2023.9.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2023.9.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2023.9.0 のリリース日は 2023年9月14日（PT）です。次回のリリースは 2023年10月5日（PT）に予定されています。

## 新着情報 {#what-is-new}

* このリリースは、Cloud Manager のバグ修正のみで構成されています。

## バグ修正 {#bug-fixes}

* プログラムを削除すると、関連する実行中のパイプラインも削除され、パイプラインが失敗ステータスと誤って指定されないようにします。
* パイプラインの実行のすべてのステップが「完了」した場合、パイプラインのステータスが「実行中」と見なされ、停止状態になっているように見えることがあります。 「完了」と表示されます。
* コードジェネレーターアーキタイプを使用して生成されたリポジトリブランチの場合、CI/CD パイプラインは失敗します。
