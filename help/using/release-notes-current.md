---
title: リリースノート（2021.8.0）
description: このページでは、Cloud Manager リリース 2021.8.0 について説明します。
feature: リリース情報
source-git-commit: 510c523423a8d7cf9ad4c5ba2af11ff12df2b1cc
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 53%

---

# リリースノート（2021.8.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.8.0 の一般リリースノートの概要を説明します。

>[!NOTE]
>AEM as a Cloud Service での Cloud Manager の最新のリリースノートについては、[現在のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.8.0 のリリース日は 2021 年 8 月 12 日（PT）です。次回のリリースは2021年9月9日に予定されています。

## 新機能 {#whats-new}

* ユーザーがCloud Manager UIを使用して複数のリポジトリを作成および管理できるセルフサービス機能。

* SonarQubeはGit履歴データを不必要に読み取っていました。 大規模なコードベースでは、これにより、不要なビルドパフォーマンスの低下が生じる可能性があります。

* パイプラインごとにMaven依存関係キャッシュを無効にするAPIが追加されました。

* Cloud Manager で使用される AEM プロジェクトアーキタイプのバージョンが 28 に更新されました。

## バグ修正 {#bug-fixes}

* 何らかの理由でパイプラインが2回トリガーされた場合、*はパイプライン実行ステータス*&#x200B;を更新できませんでしたが、実行の1つが失敗することがあります。
