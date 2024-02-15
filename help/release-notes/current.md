---
title: 2024.1.0 のリリースノート
description: Cloud Manager リリース 2024.1.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b5907179d3de329e8b86546bb8aa99608a5b351a
workflow-type: ht
source-wordcount: '257'
ht-degree: 100%

---


# Cloud Manager リリース 2024.1.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2024.1.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2024.1.0 のリリース日は 2024年1月17日（PT）です。次回のリリースは 2024年2月16日（PT）の予定です。

## 早期導入プログラム {#early-adoption}

早期導入プログラムに参加して、今後の機能をテストする機会を得ることができます

### 独自の GitHub の導入 {#byo-github}

GitHub を使用してリポジトリを管理している場合は、[Cloud Manager を通じて GitHub リポジトリ内でコードを直接検証できるようになりました。](/help/managing-code/byo-github.md)この統合により、コードを Adobe リポジトリと一貫して同期する必要がなくなり、プルリクエストをメインブランチに結合する前に検証できるようになります。この機能は、パブリック GitHub 専用です。自己ホスト型 GitHub のサポートは利用できません。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから `Grp-CloudManager_BYOG@adobe.com` にメールを送信してください。

## バグの修正 {#bug-fixes}

* テストアプリケーションがデータをどう解釈したかによってダウンロードが失敗し、合計エラー率がテストで不合格となる、いくつかの特殊なケースのエラーを修正しました。
* `BUILD_MAVEN_TRANSFER_ARTIFACT_ERROR` によりビルドステップが `FAILED` ステータスで終了した場合、宛先分岐との結合の競合によるエラーとして、適切に記述されるようになりました。
