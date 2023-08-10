---
title: 2023.8.0 のリリースノート
description: Cloud Manager リリース（2023.8.0）のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: f930f12b5f50dd96a1677ff7a56cf0e92a400556
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 39%

---


# Cloud Manager リリース（2023.8.0）のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース（2023.8.0）のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2023.8.0 のリリース日は 2023年8月10日（PT）です。次回のリリースは 2023年7月9日（PT）に予定されています。

## 新機能 {#what-is-new}

* Cloud Manager UI でのエラーメッセージの理解しやすく表示を改善するための機能強化がおこなわれました。

## バグの修正 {#bug-fixes}

* まれに起こる [コンテンツコピー](/help/using/content-copy.md) 停止しているプロセスに対処しました。
* New Relic Oneを使用しないお客様に対して、一時的なテストの問題が解決されました。
* [カスタムコード品質ルール](/help/using/custom-code-quality-rules.md) `SupportedRunmode` および `ImmutableMutableMixedPackage` AEM as a Cloud Serviceにのみ適用できるので、SonarQube から削除されました。
* 実行中のように見えるパイプラインの停止は発生しなくなりました。
* The **環境** トリガー後にメニューが閉じるようになりました **[コンテンツをコピー](/help/using/content-copy.md)** モーダルです。
* [パイプラインの再実行](/help/using/code-deployment.md#reexecute-deployment) は、以前の実行に `commitId` ビルドフェーズの状態に設定します。
* ユーザーが **アクティビティ** または **パイプライン** スクリーン。
