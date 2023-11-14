---
title: リリースノート（2023.11.0）
description: Cloud Manager リリース 2023.11.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: c7803c75bcfcc967877808214704c5746015481d
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 23%

---


# Cloud Manager リリース 2023.11.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2023.11.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2023.11.0 のリリース日は 2023年11月14日（PT）です。次回のリリースは 2023年12月7日（PT）に予定されています。

## 新機能 {#what-is-new}

* [パイプライン実行の詳細ページ](/help/using/managing-pipelines.md#view-details) が、まだ開始されていないステップが灰色表示になった状態で、パイプライン実行のすべてのステップを表示するようになりました。
* 両方で **[アクティビティ](/help/using/managing-pipelines.md#activity)** および **[パイプライン](/help/using/managing-pipelines.md#pipelines)** 実行中ステータスのパイプラインをクリックしたときに、パイプライン実行の概要を表示できるようになりました。
* 新しい **期間** セクションが [パイプラインの詳細ページ](/help/using/managing-pipelines.md#view-details) この期間には、そのプログラムの過去のトレンドに基づく、パイプラインステップの平均期間が含まれます。
* パイプライン実行ページで、完了したステップに期間が表示されるようになりました
* Cloud Manager [コンテンツコピーツール](/help/using/content-copy.md) を使用すると、可変コンテンツを AMS でホストされているAEM 6.x の実稼動環境から低い環境にオンデマンドでコピーして、テスト目的でコピーできます。

## 早期採用プログラム {#early-adoption}

初期の採用プログラムに参加し、今後の機能をテストする機会を得る

### 独自の GitHub を持ち込む {#byo-github}

GitHub を使用してリポジトリを管理する場合は、 [Cloud Manager を使用して、GitHub リポジトリ内で直接コードを検証できるようになりました。](/help/managing-code/byo-github.md) この統合により、コードをAdobeリポジトリと一貫して同期する必要がなくなり、プルリクエストを確認してからメインブランチにマージできます。

この新機能のテストとフィードバックの共有に関心がある場合は、に電子メールを送信してください。 `Grp-CloudManager_BYOG@adobe.com` Adobe IDに関連付けられた電子メールアドレスから。

### カスタム権限 {#custom-permissions}

[Cloud Manager のカスタム権限](/help/using/custom-permissions.md) では、設定可能な権限を持つ新しいカスタム権限プロファイルを作成して、Cloud Manager ユーザーのプログラム、パイプライン、環境へのアクセスを制限できます。

この新機能のテストやフィードバックの共有に関心がある場合は、電子メールでお問い合わせください `Grp-CloudManager_ams_custompermissions@adobe.com` Adobe IDに関連付けられた電子メールアドレスから。
