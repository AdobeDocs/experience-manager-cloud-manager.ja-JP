---
title: Cloud Manager 2024.12.0 のリリースノート
description: Adobe Managed Services の Cloud Manager 2024.12.0 のリリースについて説明します。
feature: Release Information
exl-id: 811567af-66c9-4c1f-ae9e-60603b70ef80
source-git-commit: 60db60be95318ebf6f2af91a94a9475604a15003
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 87%

---

# Adobe Managed Services の Cloud Manager 2024.12.0 のリリースノート {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Adobe Managed Services の [!UICONTROL Cloud Manager] 2024.12.0 のリリースについて説明します。

>[!NOTE]
>
>詳しくは、[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)を参照してください。

## リリース日 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2024.12.0 のリリース日は 2024年12月5日（PT）です。

次回のリリース予定は 2025年1月23日（PT）です。

## 新機能 {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* 2025 年 2 月 13 日木曜日（PT）より、Cloud Manager コード品質ステップで、アップグレードされた SonarQube バージョン 9.9.5.90363 が使用されるようになりました。

  [ このリンク ](/help/using/code-quality-testing.md#code-quality-testing-step) で AMS で使用可能な更新されたルールにより、Cloud Manager パイプラインのセキュリティスコアとコード品質が決まります。 この更新は、品質ゲートに影響を与え、デプロイメントをブロックする可能性があります。

## 早期導入プログラム {#early-adoption}

Cloud Manager の早期導入プログラムに参加すると、今後の機能をテストする機会を得ることができます。

### 独自の Git の導入 - GitLab と Bitbucket をサポートするようになりました {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**独自の Git の導入**&#x200B;機能が拡張され、GitLab や Bitbucket などの外部リポジトリのサポートが含まれるようになりました。この新しいサポートは、プライベートおよびエンタープライズ GitHub リポジトリに対する既存のサポートに追加されます。これらの新しいリポジトリを追加すると、パイプラインに直接リンクすることもできます。これらのリポジトリは、パブリッククラウドプラットフォーム上や、プライベートクラウドまたはインフラストラクチャ内でホストできます。また、この統合により、Adobe リポジトリと常にコード同期を行う必要がなくなり、プルリクエストをメイン分岐に結合する前に検証できるようになります。

外部リポジトリ（GitHub でホストされているリポジトリを除く）を使用するパイプラインと、**Git 変更時**&#x200B;に設定した&#x200B;**デプロイメントトリガー**&#x200B;が自動的に開始されるようになりました。

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
