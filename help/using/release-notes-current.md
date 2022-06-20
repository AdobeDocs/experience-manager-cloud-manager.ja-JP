---
title: リリースノート（2022.6.0）
description: Cloud Manager リリース 2022.6.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: dab08a2499b521b7026ab2bd17b82cb241f26fb6
workflow-type: ht
source-wordcount: '183'
ht-degree: 100%

---


# Cloud Manager リリース 2022.6.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2022.6.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2022.6.0 のリリース日は 2022年6月9日（PT）です。次回のリリースは 2022年6月30日（PT）に予定されています。

## 新機能 {#what-is-new}

* Cloud Manager ランディングページの新しいウェルカムカードでは、テナントに関連するオンボーディングチュートリアルや進行状況指標にすばやくアクセスできます。
   * この機能は、2022.06.0 リリースの後、1 週間にわたって段階的アプローチで展開されます。
* Git ミラーリングの使用時に、[ビルドアーティファクトを再利用できるようになりました](/help/using/setting-up-project.md#build-artifact-reuse)。

## API の変更点 {#api-changes}

* [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms) API は非推奨（廃止予定）となりましたので、代わりに [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) を使用してください。
   * `List Programs` は引き続き機能しますが、この機能を使用すると、ログに警告メッセージが表示されます。
   * 3 か月後にはサポートされなくなります。
