---
title: Cloud Manager 2024.10.0 のリリースノート
description: Cloud Manager 2024.10.0 のリリースノートについて説明します。
feature: Release Information
source-git-commit: 74e8f7c0f3896e0e33a02b62c003db322c0d50d8
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 27%

---

# Cloud Manager 2024.10.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] 2024.10.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)を参照してください。



## リリース日 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2024.10.0 のリリース日は 2024 年 10 月 3 日です。

次回のリリースは 2024年11月14日（PT）に予定されています。



## 新機能 {#what-is-new}

* <!-- BOTH CS & AMS --> Cloud Managerで使用されるAEM アーキタイプのバージョンが、バージョン 26 に更新されました。 [https://github.com/adobe/aem-project-archetype/releasesを参照してください ](https://github.com/adobe/aem-project-archetype/releases)
<!-- (CMGR-59817) -->



## 早期導入プログラム {#early-adoption}

Cloud Managerの早期導入プログラムに参加して、今後の機能をテストする機会を得ます。

### 独自の Git の導入 – GitLab と Bitbucket をサポート {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**独自の Git を取り込む** 機能が拡張され、GitLab や Bitbucket などの外部リポジトリがサポートされるようになりました。 この新しいサポートは、プライベートおよびエンタープライズ GitHub リポジトリの既存のサポートに加わるものです。 これらの新しいリポジトリを追加する際に、パイプラインに直接リンクすることもできます。 これらのリポジトリは、パブリッククラウドプラットフォーム上、またはプライベートクラウドやインフラストラクチャ内でホストできます。 また、この統合により、Adobeリポジトリとの継続的なコード同期が不要になり、メインブランチにマージする前にプルリクエストを検証できるようになります。

[Cloud Managerでの外部リポジトリの追加 ](/help/managing-code/external-repositories.md) を参照してください。

![リポジトリを追加ダイアログボックス](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>現在、標準のプルリクエストコード品質チェックは、GitHub でホストされるリポジトリ専用ですが、この機能を他の Git ベンダーに拡張する更新が現在進行中です。

この新機能のテストやフィードバックの提供に関心がある場合は、Adobe IDに関連付けられたメールアドレスから [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) にメールを送信してください。 使用する Git プラットフォームと、プライベート/パブリックまたはエンタープライズリポジトリ構造のいずれを使用しているかをを必ず含めてください。

### ステージング専用パイプラインと実稼動専用パイプライン {#staging-production-only-pipelines}

Adobeは、[ ステージング専用パイプラインと実稼動専用パイプライン ](/help/using/stage-prod-only.md) のサポートを導入することをお知らせします。 この新機能により、フルスタックの実稼動デプロイメントパイプラインをより小さな、より特殊なデプロイメントに分割できます。

この機能をテストしてフィードバックを提供したい場合は、Adobe IDに関連付けられたメールアドレスから [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) にメールを送信してください。

<!-- ## Bug fixes

* text
-->

<!-- Known Issues {#known-issues}

 -->
