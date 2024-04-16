---
title: リリースノート（2024.4.0）
description: Cloud Manager リリース 2024.4.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 4a7c6fbc3fa936ff1470420966823f94fb3a4d7b
workflow-type: ht
source-wordcount: '258'
ht-degree: 100%

---


# Cloud Manager リリース 2024.4.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2024.4.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2024.4.0 のリリース日は 2024年4月10日（PT）です。次回のリリースは 2024年5月9日（PT）に予定されています。

## 新機能 {#what-is-new}

* ステージング専用パイプラインと実稼動専用パイプラインのサポートが導入され、フルスタックの実稼動デプロイメントパイプラインをより小さな特殊なデプロイメントに分割できるようになりました。
* コードのビルドの問題に対するエラーメッセージが強化され、根本原因と次の実行可能な手順を簡単に特定できます。

## 早期導入プログラム {#early-adoption}

早期導入プログラムに参加して、今後の機能をテストする機会を得ることができます

### 独自の GitHub の導入 {#byo-github}

GitHub を使用してリポジトリを管理している場合は、[Cloud Manager を通じて GitHub リポジトリ内でコードを直接検証できるようになりました。](/help/managing-code/byo-github.md)この統合により、コードを Adobe リポジトリと一貫して同期する必要がなくなり、プルリクエストをメインブランチに結合する前に検証できるようになります。この機能は、パブリック GitHub 専用です。自己ホスト型 GitHub のサポートは利用できません。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから `Grp-CloudManager_BYOG@adobe.com` にメールを送信してください。

## バグの修正 {#bug-fixes}

* Cloud Manager が間違ったコミットハッシュを持つアーティファクトを再利用するバグに対処しました。
