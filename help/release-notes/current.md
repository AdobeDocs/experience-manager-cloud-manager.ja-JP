---
title: Cloud Manager 2025.8.0 のリリースノート
description: Adobe Managed Services の Cloud Manager 2025.8.0 のリリースについて説明します。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: b64b8529e4c6072c9bcb7438dc2d89098d29115d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 61%

---

# Adobe Managed Services の Cloud Manager 2025.8.0 のリリースノート {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Services の [!UICONTROL Cloud Manager] 2025.8.0 のリリースについて説明します。

[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)も参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] 2025.8.0 のリリース日は 2025年8月7日（PT）です。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

次回のリリース予定は 2025年9月4日（PT）です。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## 新機能 {#what-is-new}

* **Adobe Experience Hub近日公開予定**

  2025 年 8 月 19 日（PT）より、AdobeはすべてのAdobe Experience Manager ユーザーに対して新しいExperience Hubの段階的なロールアウトを開始します。

  Experience Hubは、状況に応じたパーソナライズされたエクスペリエンスを提供し、ユーザーの目標達成を支援する統合的な出発点です。 このロールアウトは 2025 年 8 月 26 日（PT）までに終了し、すべてのユーザーが使用できるようになります。 新しいExperience Hubには、[experience.adobe.com](https://experience.adobe.com/) から直接アクセスできます。 詳しくは、[Adobe Experience Hub](/help/experience-hub.md) を参照してください。

* **ステージング専用パイプラインと実稼動専用パイプライン**

  Cloud Managerでは、ステージング専用パイプラインと実稼動専用パイプラインをサポートするようになりました。 この機能を使用すると、フルスタックの実稼動デプロイメントを、より小さな目的別のパイプラインに分割できます。<!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![ 「フルスタックコード」ラジオボタンと「ステージ環境」が選択された状態の「実稼動以外のパイプラインを追加」ダイアログボックス ](/help/release-notes/assets/add-non-production-pipeline.png)

  [ ステージング専用および実稼動専用パイプライン ](/help/using/stage-prod-only.md) を参照してください。

* **お気に入りのパイプライン**

  このリリースでは、Cloud Managerでお気に入りのパイプラインをピン留めし、特定のパイプラインをお気に入りとしてマークして、「**パイプライン**」ページのリストの上部に表示できるようになりました。 この機能強化により、頻繁にアクセスするパイプラインをより容易に見つけて実行しやすくなっています。<!-- CMGR-68293 -->

  ![お気に入りとしてマークされたパイプライン](/help/release-notes/assets/pipeline-favorites.png)*お気に入りとしてマークされた 2 つのパイプライン。*

  [パイプラインのお気に入りをマークする](/help/using/managing-pipelines.md#pipeline-favorites)を参照してください。


## Beta プログラム {#beta-program}

Cloud ManagerのBeta プログラムに参加すると、一般リリース前に今後リリースされる機能を独占的に利用できます。

現在、以下の機能が利用可能です。


### 独自の Git の導入（BYOG） {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Azure DevOps Git リポジトリを Cloud Manager にオンボードできるようになりました。これは、最新の Azure DevOps リポジトリとレガシー VSTS（Visual Studio Team Services）リポジトリの両方に対応しています。

* Edge Delivery Services のユーザーは、オンボードされたリポジトリを使用して、サイトコードを同期およびデプロイできます。
* AEM as a Cloud Service および Adobe Managed Services（AMS）のユーザーは、リポジトリをフルスタックパイプラインとフロントエンドパイプラインの両方にリンクできます。

追加のパイプラインタイプと、コード品質パイプラインを通じたプルリクエスト検証のサポートは、近日リリース予定です。

[Cloud Manager でのプライベートリポジトリの追加](/help/managing-code/external-repositories.md)を参照してください。

![リポジトリを追加ダイアログボックス](/help/release-notes/assets/azure-repo.png)

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) にメールを送信します。 使用する Git プラットフォームと、プライベート／パブリックまたはエンタープライズリポジトリ構造のいずれを使用するかを必ず含めてください。

#### アクセストークンを管理{#manage-access-tokens}

Cloud Managerで「**アクセストークンの管理**」を使用して、外部 BYOG リポジトリ (GitHub Enterprise、GitLab、Bitbucket、Azure DevOps など) に関連付けられたアクセストークンを表示、名前変更、削除します。

[アクセストークンを管理](/help/managing-code/manage-access-tokens.md)をご覧ください。

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## バグ修正 {#bug-fixes}

7 月のCloud Manager リリースには重要なバグ修正はありません。

<!--
Known Issues {#known-issues}

* A -->
