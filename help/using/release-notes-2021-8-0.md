---
title: リリースノート（2021.8.0）
description: このページでは、Cloud Manager リリース 2021.8.0 について説明します。
feature: Release Information
source-git-commit: 3fccb0b577662ebc12b65777cbf9624e06d4259d
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 100%

---

# リリースノート（2021.8.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.8.0 の一般リリースノートの概要を説明します。

>[!NOTE]
>AEM as a Cloud Service での Cloud Manager の最新のリリースノートについては、[現在のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.8.0 のリリース日は2021年8月12日（PT）です。


## 新機能 {#whats-new}

* ユーザーが Cloud Manager UI を使用して複数のリポジトリを作成および管理できるセルフサービス機能。

* SonarQube は git 履歴データを不必要に読み取っていました。大規模なコードベースでは、これにより、ビルドパフォーマンスが不必要に低下することがありました。

* パイプラインごとに Maven 依存関係キャッシュを無効にする API が追加されました。

* Cloud Manager で使用される AEM プロジェクトアーキタイプのバージョンが 29 に更新されました。

## バグ修正 {#bug-fixes}

* 何らかの理由でパイプラインが 2 回トリガーされた場合、「*パイプライン実行ステータスを更新できませんでした*」エラーで、いずれかの実行が失敗します。
