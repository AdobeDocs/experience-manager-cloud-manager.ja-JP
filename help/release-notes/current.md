---
title: リリースノート（2024.2.0）
description: Cloud Manager リリース 2024.2.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: cc87246503ab63d6dd60c691f15fc4759fcf6939
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 61%

---


# Cloud Manager リリース 2024.2.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2024.2.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース 2024.2.0 は 2024 年 2 月 15 日です。 次回のリリースは 2024 年 3 月 16 日に予定されています。

## 新機能 {#what-is-new}

* の一部として [デプロイメント](/help/using/code-deployment.md) Dispatcher キャッシュは、 **Dispatcher の添付** 手順 アプリケーションロードバランサーにコードをデプロイした後、各ノードで変更をテストできるように、特定のパブリッシャーにコードをデプロイした後、Dispatcher をロードバランサーにアタッチする前に、関連する Dispatcher から直接変更をテストできます。
* [ビルド環境](/help/getting-started/build-environment.md) は、Maven バージョン 3.9.4 および JDK バージョン jdk-11.0.22 および jdk1.8.0_401 に更新されました。

## 早期導入プログラム {#early-adoption}

早期導入プログラムに参加して、今後の機能をテストする機会を得ることができます

### 独自の GitHub の導入 {#byo-github}

GitHub を使用してリポジトリを管理している場合は、[Cloud Manager を通じて GitHub リポジトリ内でコードを直接検証できるようになりました。](/help/managing-code/byo-github.md)この統合により、コードを Adobe リポジトリと一貫して同期する必要がなくなり、プルリクエストをメインブランチに結合する前に検証できるようになります。この機能は、パブリック GitHub 専用です。自己ホスト型 GitHub のサポートは利用できません。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから `Grp-CloudManager_BYOG@adobe.com` にメールを送信してください。

## バグの修正 {#bug-fixes}

* ビルドコンテナの JDK が、解決するバージョンに更新されました。 [JDK-8313765。](https://bugs.openjdk.org/browse/JDK-8313765)
§