---
title: Cloud Manager 2026.11.0のリリースノート
description: Adobe Managed ServicesのCloud Manager 2026.11.0のリリースについて説明します。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: 'https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro'
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: b48085c8209c0802f6f2d321865bd1a1ee786139
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 10%
---

# Adobe Managed ServicesのCloud Manager 2026.11.0のリリースノート {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Servicesの[!UICONTROL Cloud Manager] 2026.11.0のリリースについて説明します。

[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)も参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] 2026.11.0のリリース日は2026年11月5日木曜日です。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

次回のリリース予定は2026年12月3日木曜日です。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新機能 {#new-features}

### AEM Managed Servicesのweb階層パイプライン {#web-tier-pipelines}

Cloud Managerでは、AMS プログラム用の専用のWeb階層パイプラインがサポートされるようになりました。これにより、フルスタックのデプロイとは独立して、Dispatcherおよびweb階層設定をデプロイできます。 これにより、web層の変更の迅速な反復と、不要なパイプライン全体の実行の削減が可能になります。

Web階層パイプラインが設定されている場合、フルスタックパイプラインは、デプロイメントの競合を防ぐために、その環境のweb階層デプロイメントを自動的にスキップします。 Web階層パイプラインを削除すると、デフォルトのデプロイメント動作が自動的に復元されます。<!-- CMGR-27553 -->

[Web階層設定パイプライン ](/help/overview/ci-cd-pipelines.md#web-tier-config-pipelines)を参照してください。

## Beta プログラム {#beta-program}

現時点で利用可能なベータプログラムの機会はありません。

<!--
To get exclusive access to upcoming features before their general release, participate in Cloud Manager's beta programs.

>[!IMPORTANT]
>
>Beta releases contain issues and are provided without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify or otherwise support (through Adobe Support Services or otherwise) the beta releases. Customers use beta releases at their own risk. Do not rely on the correct functioning or performance of beta releases, or on any accompanying documentation or materials. Features and APIs in beta are subject to change without notice. Any use of the beta releases is entirely at the customer's own risk.

The following beta program opportunity is currently available:
-->

## バグ修正 {#bug-fixes}


* 大規模なプロジェクトでコード品質スキャンが失敗する。 コード品質（SonarQube）スキャンは、マルチギガバイトのデバッグログを生成し、特定のバンドルライブラリをスキャンしてビルドに失敗すると強制終了されます。 スキャンが修正され、影響を受けるプロジェクトで正常に完了するようになりました。 （CMGR-80025）

* サイトの使用状況CSVの書き出しでは、月のラベルが1か月ずつ変更されました。 ライセンス/サイト使用状況の詳細ページでは、CSV書き出しに、UTCより後のタイムゾーンのユーザーに対して1か月早くシフトされた月ラベルが表示されます。 書き出しでは、ユーザーのタイムゾーンに関係なく、正しい月ラベルが表示されるようになりました。 （CMGR-80903）

* アクセストークン名を再利用しても、既存のトークンは上書きされなくなりました。 プログラム内で既存のアクセストークン名を再利用すると、共有トークンが上書きされ、重複したアクセストークンが作成されます。 Cloud Managerで、トークン名の再利用を正しく処理できるようになりました。これにより、誤った上書きや重複を防ぐことができます。 （CMGR-81236）


<!--
Known Issues {#known-issues}
-->
