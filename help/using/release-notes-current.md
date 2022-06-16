---
title: リリースノート（2022.6.0）
description: Cloud Manager リリース 2022.6.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: dab08a2499b521b7026ab2bd17b82cb241f26fb6
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 42%

---


# Cloud Manager リリース 2022.6.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2022.6.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース 2022.6.0 は 2022 年 6 月 9 日です。 次回のリリースは 2022年6月30日（PT）に予定されています。

## 新機能 {#what-is-new}

* Cloud Manager ランディングページの新しいウェルカムカードでは、テナントに関連するオンボーディングチュートリアルや進行状況指標にすばやくアクセスできます。
   * この機能は、2022.06.0リリース以降の週にわたって段階的なアプローチで展開されます。
* [ビルドアーティファクトを再利用できるようになりました](/help/using/setting-up-project.md#build-artifact-reuse) git ミラーリングを使用する場合。

## API の変更点 {#api-changes}

* この [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms) API は廃止され、 [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) 代わりにを使用する必要があります。
   * `List Programs` は引き続き機能しますが、この機能を使用すると、ログに警告メッセージが表示されます。
   * 3 ヶ月後はサポートされなくなります。
