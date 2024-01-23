---
title: 2024.1.0 のリリースノート
description: Cloud Manager リリース 2024.1.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b235e398b42e9da3dd2efacdc0ef38b6803bd213
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 68%

---


# Cloud Manager リリース 2024.1.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2024.1.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース 2024.1.0 は 2024 年 1 月 17 日です。 次回のリリースは 2024 年 2 月 16 日に予定されています。

## 早期導入プログラム {#early-adoption}

早期導入プログラムに参加して、今後の機能をテストする機会を得ることができます

### 独自の GitHub の導入 {#byo-github}

GitHub を使用してリポジトリを管理している場合は、[Cloud Manager を通じて GitHub リポジトリ内でコードを直接検証できるようになりました。](/help/managing-code/byo-github.md)ここの統合により、コードを Adobe リポジトリと一貫して同期する必要がなくなり、プルリクエストをメインブランチに結合する前に検証できるようになります。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから `Grp-CloudManager_BYOG@adobe.com` にメールを送信してください。

## バグの修正 {#bug-fixes}

* テストアプリケーションでデータがどのように解釈されるかが原因でダウンロードが失敗し、合計エラー率がテストに失敗する場合があると、エラーが修正されました。
* ビルドステップが「 」ステータスで終了したとき `FAILED` 原因は `BUILD_MAVEN_TRANSFER_ARTIFACT_ERROR`の場合、宛先ブランチとの結合の競合が原因でエラーとして適切に説明されるようになりました。
