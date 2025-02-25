---
title: Cloud Manager 2025.2.0 のリリースノート
description: Adobe Managed Services の Cloud Manager 2025.2.0 のリリースについて説明します。
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 51dd060ec9b922ace9ce537cac669c61154284e8
workflow-type: ht
source-wordcount: '241'
ht-degree: 100%

---

# Adobe Managed Services の Cloud Manager 2025.2.0 のリリースノート {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

Adobe Managed Services の [!UICONTROL Cloud Manager] 2025.2.0 のリリースについて説明します。

[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)も参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] 2025.2.0 のリリース日は 2025年2月13日（PT）です。

次回のリリース予定は 2025年3月13日木曜日（PT）です。

## 新機能 {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* **アップグレードされた SonarQube**

  2025年2月13日木曜日（PT）以降、Cloud Manager コード品質ステップでは、SonarQube 9.9.5.90363 が使用されるようになりました。

  [このリンク](/help/using/code-quality-testing.md#code-quality-testing-step)の AMS に使用可能な更新されたルールにより、Cloud Manager パイプラインのセキュリティスコアとコード品質が決定されます。

* SonarQube 9.9 は、すべてのお客様に対するデフォルトのコード品質スキャンエンジンになりました。

* **Java 17 および Java 21 ビルド環境のサポート**

  お客様は、オプションで Java 17 または Java 21 を使用してビルドし、パフォーマンス向上と新しい言語機能のメリットを享受できます。Maven プロジェクトの説明と特定のライブラリバージョンのアップデートを含む設定手順について詳しくは、[ビルド環境](/help/getting-started/build-environment.md)を参照してください。

  >[!NOTE]
  >Cloud Service 環境の場合、ビルドバージョンを Java 17 または Java 21 に設定した際、ランタイムはデフォルトで Java 21 です。

* **コンテンツのコピー検証の強化**

  コンテンツのコピー検証ルールが更新されました。このリリースでは、ソース環境または宛先環境のいずれかでアクティブなパイプライン実行がある場合、ユーザーはコンテンツのコピーをトリガーできなくなりました。ユーザーは、コンテンツのコピーを開始する前に、進行中のすべてのパイプライン実行が完了するまで待機する必要があります。

<!-- 
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features.

### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

The **Bring Your Own Git** feature has been expanded to include support for external repositories, such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

Pipelines using external repositories (excluding GitHub-hosted ones) and the **Deployment Trigger** set to **On Git Changes** now start automatically.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
