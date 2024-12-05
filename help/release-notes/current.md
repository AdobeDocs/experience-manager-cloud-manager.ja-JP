---
title: Cloud Manager 2024.12.0 のリリースノート
description: Adobe Managed ServicesのCloud Manager 2024.12.0 のリリースについて説明します。
feature: Release Information
source-git-commit: ee79124a012106e53ffaaf9462202712f7078809
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 65%

---

# AdobeManaged ServicesのCloud Manager 2024.12.0 のリリースノート {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

AdobeManaged Servicesの [!UICONTROL Cloud Manager] 2024.12.0 のリリースについて説明します。

>[!NOTE]
>
>詳しくは、[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)を参照してください。

## リリース日 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2024.12.0 のリリース日は 2024 年 12 月 5 日です。

次回のリリース予定は 2025年1月23日（PT）です。

## 新機能 {#what-is-new}

* AEMのコード品質ステップで、古い 7.4 バージョンに代わって、SonarQube 9.9 サーバーが使用されるようになりました。 このアップグレードにより、セキュリティ、パフォーマンス、コード品質のチェックがさらに強化され、プロジェクトに対するより包括的な分析とカバレッジが提供されます。<!-- CMGR-45683 -->

## 早期導入プログラム {#early-adoption}

Cloud Manager の早期導入プログラムに参加すると、今後の機能をテストする機会を得ることができます。

### 独自の Git の導入 - GitLab と Bitbucket をサポートするようになりました {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**独自の Git を取り込む** 機能が拡張され、GitLab や Bitbucket などの外部リポジトリがサポートされるようになりました。 この新しいサポートは、プライベートおよびエンタープライズ GitHub リポジトリに対する既存のサポートに追加されます。これらの新しいリポジトリを追加すると、パイプラインに直接リンクすることもできます。これらのリポジトリは、パブリッククラウドプラットフォーム上や、プライベートクラウドまたはインフラストラクチャ内でホストできます。また、この統合により、Adobe リポジトリと常にコード同期を行う必要がなくなり、プルリクエストをメイン分岐に結合する前に検証できるようになります。

外部リポジトリ（GitHub でホストされているリポジトリを除く）と **Git の変更時** に設定された **デプロイメントトリガー** を使用したパイプラインが自動的に開始されるようになりました。

[Cloud Manager でのプライベートリポジトリの追加](/help/managing-code/external-repositories.md)を参照してください。

![リポジトリを追加ダイアログボックス](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>現在、標準のプルリクエストコード品質チェックは、GitHub でホストされるリポジトリ専用ですが、この機能を他の Git ベンダーに拡張する更新が進行中です。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) にメールを送信します。使用する Git プラットフォームと、プライベート／パブリックまたはエンタープライズリポジトリ構造のいずれを使用するかを必ず含めてください。


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
