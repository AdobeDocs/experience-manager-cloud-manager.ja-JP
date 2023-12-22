---
title: 2023.12.0 のリリースノート
description: Cloud Manager リリース 2023.12.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 2ac254508e4015fea21c4fcd087703ac5fbeeec6
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 70%

---


# Cloud Manager リリース 2023.12.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2023.12.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2023.12.0 のリリース日は 2023年12月14日（PT）です。次回のリリースは 2024年1月18日（PT）の予定です。

## 新機能 {#what-is-new}

* [Cloud Manager のカスタム権限](/help/using/custom-permissions.md)を使用すると、Cloud Manager ユーザーのプログラム、パイプライン、環境へのアクセスを制限する設定可能な権限を持つ新しいカスタム権限プロファイルを作成できます。
* 更新のロールアウト： [ビルド環境](/help/getting-started/build-environment.md) それは [10 月の Cloud Manager リリースで発表および開始された](/help/release-notes/2023/2023-10-0.md) が完了しました。
   * ノード 18 のサポートが、 [フロントエンドパイプラインとフルスタックパイプライン。](/help/overview/ci-cd-pipelines.md)
   * Java 8 のマイナーバージョンがに更新されました。 `jdk1.8.0_371`.
   * Java 11 のマイナーバージョンがに更新されました。 `jdk-11.0.20`.
   * Maven がバージョン 3.8.8 に更新されました。
      * Maven でセキュリティで保護されていないすべてのを無効化 `http://*` デフォルトではミラーされます。
      * [Adobeが推奨](/help/getting-started/build-environment.md#https-maven) ユーザーは、HTTP の代わりに HTTPS を使用するように Maven リポジトリを更新します。
* ビルドコンテナのベースイメージが Ubuntu 22.04 に更新されました。

## 早期導入プログラム {#early-adoption}

早期導入プログラムに参加して、今後の機能をテストする機会を得ることができます

### 独自の GitHub の導入 {#byo-github}

GitHub を使用してリポジトリを管理している場合は、[Cloud Manager を通じて GitHub リポジトリ内でコードを直接検証できるようになりました。](/help/managing-code/byo-github.md)ここの統合により、コードを Adobe リポジトリと一貫して同期する必要がなくなり、プルリクエストをメインブランチに結合する前に検証できるようになります。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから `Grp-CloudManager_BYOG@adobe.com` にメールを送信してください。
