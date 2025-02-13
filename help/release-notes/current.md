---
title: Cloud Manager 2025.2.0 のリリースノート
description: Adobe Managed Services の Cloud Manager 2025.2.0 のリリースについて説明します。
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 9d9bf7d689c0ace41bce3f31febe8ba78636c01f
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 93%

---

# Adobe Managed Services の Cloud Manager 2025.2.0 のリリースノート {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

Adobe Managed Services の [!UICONTROL Cloud Manager] 2025.2.0 のリリースについて説明します。

[Adobe Experience Manager as a Cloud Serviceの最新のリリースノート ](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home) も参照してください。

## リリース日 {#release-date}

*Cloud Managerの 2 月リリースには、注目すべきバグや機能はありません。*

[!UICONTROL Cloud Manager] 2025.2.0 のリリース日は 2025年2月13日（PT）です。

次回のリリース予定は 2025年3月13日木曜日（PT）です。

## 新機能 {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* 2025年2月13日木曜日（PT）以降、Cloud Manager コード品質ステップでは、アップグレードされた SonarQube バージョン 9.9.5.90363 が使用されるようになりました。

  [このリンク](/help/using/code-quality-testing.md#code-quality-testing-step)の AMS に使用可能な更新されたルールにより、Cloud Manager パイプラインのセキュリティスコアとコード品質が決定されます。 この更新は、品質ゲートに影響を与え、デプロイメントをブロックする可能性があります。

## 早期導入プログラム {#early-adoption}

Cloud Manager の早期導入プログラムに参加すると、今後の機能をテストする機会を得ることができます。

### 独自の Git の導入 - GitLab と Bitbucket をサポートするようになりました {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**独自の Git の導入**&#x200B;機能が拡張され、GitLab や Bitbucket などの外部リポジトリのサポートが含まれるようになりました。 この新しいサポートは、プライベートおよびエンタープライズ GitHub リポジトリに対する既存のサポートに追加されます。 これらの新しいリポジトリを追加すると、パイプラインに直接リンクすることもできます。 これらのリポジトリは、パブリッククラウドプラットフォーム上や、プライベートクラウドまたはインフラストラクチャ内でホストできます。 また、この統合により、Adobe リポジトリと常にコード同期を行う必要がなくなり、プルリクエストをメイン分岐に結合する前に検証できるようになります。

外部リポジトリ（GitHub でホストされているリポジトリを除く）を使用するパイプラインと、**Git 変更時**&#x200B;に設定した&#x200B;**デプロイメントトリガー**&#x200B;が自動的に開始されるようになりました。

[Cloud Manager でのプライベートリポジトリの追加](/help/managing-code/external-repositories.md)を参照してください。

![リポジトリを追加ダイアログボックス](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>現在、標準のプルリクエストコード品質チェックは、GitHub でホストされるリポジトリ専用ですが、この機能を他の Git ベンダーに拡張する更新が進行中です。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) にメールを送信します。 使用する Git プラットフォームと、プライベート／パブリックまたはエンタープライズリポジトリ構造のいずれを使用するかを必ず含めてください。


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
