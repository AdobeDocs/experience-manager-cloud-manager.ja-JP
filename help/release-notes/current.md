---
title: Cloud Manager 2025.9.0 のリリースノート
description: Adobe Managed Services の Cloud Manager 2025.9.0 のリリースについて説明します。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 24ec1d82f9a700b57cd74c2c83c8d9d00b8bece1
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 72%

---

# Adobe Managed Services の Cloud Manager 2025.9.0 のリリースノート {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Services の [!UICONTROL Cloud Manager] 2025.9.0 のリリースについて説明します。

[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)も参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] 2025.9.0 のリリース日は 2025年9月4日（PT）です。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

次回のリリース予定は 2025年10月2日木曜日（PT）です。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## 新機能 {#what-is-new}

* **Azure DevOps （プライベートリポジトリ）のサポートが追加されました**

  ドキュメントの更新には、Azure DevOps で独自の Git を取り込むための設定手順や、プルリクエストの検証が含まれています。 [Cloud Managerへの外部リポジトリの追加 ](/help/managing-code/external-repositories.md) を参照してください。

* **独自の Git （BYOG）サポートを設定パイプライン（プライベートリポジトリ）に拡張**

  Cloud Managerは、GitHub、Bitbucket、Azure DevOps、GitLab をまたいだプライベートリポジトリを使用した設定パイプラインをサポートするようになりました。 このサポートにより、開発サイクルがさらに加速します。 ![ プライベートリポジトリのプルリクエストチェック ](/help/managing-code/github-check-config.md) を参照してください。

## Beta プログラム {#beta-program}

Cloud ManagerのBeta プログラムに参加すると、一般リリース前に今後リリースされる機能を独占的に利用できます。

現在、以下の機能が利用可能です。


### Bring Your Own Git (BYOG) {#gitlab-bitbucket-azure-vsts}

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

Cloud Managerの 8 月のリリースには、重要なバグ修正はありません。

<!--
Known Issues {#known-issues}

* A -->
