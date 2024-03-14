---
title: 2024.3.0 のリリースノート
description: Cloud Manager リリース 2024.3.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 22730ba281f7c1c4720158a3a813c56b815a0af1
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 68%

---


# Cloud Manager リリース 2024.3.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2024.3.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース 2024.3.0 は 2024 年 3 月 14 日です。 次回のリリースは 2024 年 4 月 11 日に予定されています。

## 新機能 {#what-is-new}

* 緑のサーバーの IP/DNS(FQDN) 情報を含む詳細が、Cloud Manager UI に表示されるようになりました。

## 早期導入プログラム {#early-adoption}

早期導入プログラムに参加して、今後の機能をテストする機会を得ることができます

### 独自の GitHub の導入 {#byo-github}

GitHub を使用してリポジトリを管理している場合は、[Cloud Manager を通じて GitHub リポジトリ内でコードを直接検証できるようになりました。](/help/managing-code/byo-github.md)この統合により、コードを Adobe リポジトリと一貫して同期する必要がなくなり、プルリクエストをメインブランチに結合する前に検証できるようになります。この機能は、パブリック GitHub 専用です。自己ホスト型 GitHub のサポートは利用できません。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから `Grp-CloudManager_BYOG@adobe.com` にメールを送信してください。

## バグの修正 {#bug-fixes}

* エラー率指標が失敗した場合に、パフォーマンステスト手順で適切なログが生成されなかった場合に、バグが修正されました。
* サイト (404) 上にページが存在しないことを検出するタスクを負うパフォーマンステストサービス内のロジックが改善され、よりスムーズで中断のないデプロイメントが実現しました。
